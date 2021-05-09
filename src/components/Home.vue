<template>
  <h2>Filter LearnVue Articles</h2>
    <input type="text" placeholder="Filter Search" v-model="query" />
    <button @click="reset">Reset</button>
    <search-results :query="query" />

</template>



<!-- using "<script setup>" -->
<!-- To use props with <script setup> you need to call defineProps() with the component prop options as the argument-->
<!--
<script setup>
import { defineProps, reactive } from 'vue'

defineProps({
  msg: String
})

const state = reactive({ count: 0 })
</script>
  -->


<!-- without "<script setup>" + with "setup()"-->

<script >
import { ref } from "vue";
// import SearchResults from "./SearchResultsMock.vue";
// import SearchResults from "./SearchResultsAPI.vue";
import SearchResults from "./SearchResultsAPI2.vue";

export default {

  components: {
    SearchResults,
  },

  props: {
    msg: String,
  },

  setup() {
    const query = ref("");

    const reset = (evt) => {
      query.value = ""; // clears the query
    };

    return {
      query,
      reset,
    };
  },
};
</script>



<style>
#container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
input[type="text"] {
  margin-bottom: 20px;
  padding: 10px;
}
</style>
