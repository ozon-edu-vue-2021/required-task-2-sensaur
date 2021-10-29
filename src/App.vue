<template>
  <div id="app">
    <h1>Tree Browser</h1>
    <TreeBrowser
        :node="root"
    />
  </div>
</template>

<script>
import TreeBrowser from "./components/TreeBrowser";
import root from '../public/static/node_modules.json'
export default {
  name: 'App',
  data() {
    return {root: root}
  },
  components: {
    TreeBrowser,
  }
}
</script>

<style>
body{
  background-color: #333;
  color: white;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
