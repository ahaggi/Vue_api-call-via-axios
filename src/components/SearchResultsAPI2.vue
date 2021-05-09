<template>
  <div class="root">
    <h3 v-if="loading">Loading...</h3>
    <!-- Start of error alert -->
    <div v-else-if="errorState.value.message">
      <h3>{{ errorState.value.title }}</h3>
      <p>{{ errorState.value.message }}</p>
    </div>
    <!-- End of error alert -->

    <div v-else>
      <p class="info">
        Showing {{ filteredItems.length }} results for "{{ query }}"
      </p>
      <ul>
        <li v-for="item in filteredItems" :key="item.id">
          {{ item.content }}
        </li>
      </ul>
    </div>
  </div>
</template>


<script >
import axios from "axios";

import { computed, ref, reactive } from "vue";
export default {
  props: {
    query: String,
  },
  setup(props, context) {
    let dataList = ref([]);
    let loading = ref(false);
    let errorState = reactive({ title: null, message: null });

    // it's IMPORTANT to define the api call here inside "setup"
    const fetchDataFromApi = async () => {
      loading.value = true;
      errorState.value = { title: null, message: null };

      try {
        let response = await axios.get("http://127.0.0.1:5008//api/notes");
        dataList.value = response.data;
        console.log(dataList.value);

      } catch (err) {
        console.log(err);
        errorState.value = errHandler(err);
      } finally {
        loading.value = false;
      }
    };

    const filteredItems = computed(() =>
      dataList.value.filter((item) => {
        console.log("dataList");
        return item.content.toLowerCase().includes(props.query.toLowerCase());
      })
    );

    return {
      dataList,
      filteredItems,
      loading,
      errorState,
      fetchDataFromApi,
    };
  },

  created() {
    this.fetchDataFromApi();
  },
};

const errHandler = (err) => {
  if (err.response) {
    // client received an error response (5xx, 4xx)
    return {
      title: "Server Response",
      message: err.message,
    };
  } else if (err.request) {
    // client never received a response, or request never left
    return {
      title: "Unable to Reach Server",
      message: err.message,
    };
  } else {
    // There's probably an error in your code
    return {
      title: "Application Error",
      message: err.message,
    };
  }
};
</script>
<style scoped>
.root {
  width: 400px;
  margin: 0 auto;
}
.root .info p {
  text-align: right;
  font-size: 0.7em;
  margin: 0;
}
ul {
  list-style: none;
  width: 50px 0;
  padding: 0;
  background-color: #fafafa;
  border-radius: 5px;
  border: 1px solid #ddd;
}
li {
  text-align: left;
  padding: 20px;
  border-bottom: 1px solid #ddd;
}
li:nth-last-of-type(1) {
  border-bottom: none;
}
</style>
