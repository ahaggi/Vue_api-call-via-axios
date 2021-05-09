<template>
  <div class="root">
    <p>Showing {{ filteredItems.length }} results for "{{ query }}"</p>
    <ul>
      <li v-for="item in filteredItems" :key="item.id">
        {{ item.content }}
      </li>
    </ul>
  </div>
</template>


<script >
import { computed, ref } from "vue";
import dataListMock from "../mock-data.json";
export default {
  props: {
    query: String,
  },
  setup(props, context) {
    let dataList = dataListMock;

    const filteredItems = computed(() =>
      dataList.filter((item) => {
        console.log("dataList");
        return item.content.toLowerCase().includes(props.query.toLowerCase());
      })
    );

    return {
      dataList,
      filteredItems,
    };
  },


};
</script>
<style scoped>
.root {
  width: 400px;
  margin: 0 auto;
}
.root p {
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
