<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <CheckList/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import CheckList from './components/CheckList.vue'

export default {
  name: 'App',
  components: {
    CheckList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
}
ul {
  list-style-type:none;
}
</style>
