<template>
  <div id="app">
    <to-do-app />
  </div>
</template>

<script>
import ToDoApp from './components/ToDo-App.vue'

export default {
  name: 'App',
  components: {
    ToDoApp
    
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
}

body {
  margin: 0;
  padding: 0;
}
</style>
