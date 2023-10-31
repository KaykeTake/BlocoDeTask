<template>
  <div id="app">
    <MuralTask/>
  </div>
</template>

<script>
import MuralTask from "./components/MuralTask.vue";

export default {
  name: 'App',
  components: {
    MuralTask
},
data(){
      return{
      }
    },
    methods: {
  }
}
</script>

<style>
body{
  background-color: #31797A;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
