<template>
  <div id="app">
    <img src="./assets/list.png" width="20%">
    <h1>To-do リスト</h1>
    <ToDoForm />
    <ToDoList />
  </div>
</template>

<script>
var ToDoForm = require('./components/to-doForm')
var ToDoList = require('./components/to-doList')

export default {
  name: 'App',
  components: {
    ToDoForm,
    ToDoList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
