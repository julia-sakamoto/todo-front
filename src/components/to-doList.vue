<template>
  <div id="todo-list">
      <ul class="container list">
        <li>{{item.status}} {{item.title}} - {{item.date}}</li>
      </ul>
  </div>
</template>

<script>
const axios = require('axios')

export default {
  name: 'ToDoList',
  data () {
    return {
      item: []
    }
  },
  created () {
    axios.get('https://todo-server-juliasakamoto.herokuapp.com/', {
      headers: {
        'Access-Control-Allow-Origin': '*'
      }
    })
      .then((res) => {
        this.item = res.data
      })
      .catch((err) => {
        console.log(err)
      })
  }
}
</script>

<style>
.list {
  list-style: none;
  padding: 2em;
}
</style>
