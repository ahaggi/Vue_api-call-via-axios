<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <home msg="Hello Vue 3 + Vite" />
</template>

<!-- using "<script setup>" -->
<!-- To use props with <script setup> you need to call defineProps() with the component prop options as the argument-->
<!--
<script setup>
import Home from './components/Home.vue'

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
</script>
-->

<!-- without "<script setup>"  -->
<script>
import Home from './components/Home.vue'

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

}
</style>
