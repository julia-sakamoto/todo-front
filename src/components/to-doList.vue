<template>
  <div id="todo-list">
      <ul class="container list">
        <li v-for="(item, i) in items" :key="i" @click="DeleteOrUpdate(i)">
          {{item.status}} {{item.title}} - {{item.date}}
        </li>
      </ul>
  </div>
</template>

<script>
const axios = require('axios')

export default {
  name: 'ToDoList',
  data () {
    return {
      items: []
    }
  },
  mounted () {
    axios.get('https://todo-server-juliasakamoto.herokuapp.com/api/todos')
      .then((res) => {
        for (var i = 0; i < res.data.length; i++) {
          this.items.push(res.data[i])
        }
      })
      .catch((err) => {
        console.log('We got an error: ', err)
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
