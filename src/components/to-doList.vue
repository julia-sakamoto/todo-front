<template>
  <div id="todo-list">
    <p v-if="isChanged">リストが更新されました！F5を押してください。</p>
    <ul class="container list">
      <li v-for="(item, i) in items" :key="i" class="todo-row">
          {{item.status}} {{item.title}} - {{item.date}}
          <button @click="update(item)" class="btn">完了</button>
          <button @click="erase(item)" class="btn">削除</button>
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
      items: [],
      isChanged: false
    }
  },
  methods: {
    update (item) {
      axios.put('https://todo-server-juliasakamoto.herokuapp.com/api/todos', {idNum: item._id})
        .then((res) => {
          console.log(res)
        })
        .catch((err) => {
          console.log('Delete had an error: ', err)
        })
      this.isChanged = true
    },
    erase (item) {
      axios.delete('https://todo-server-juliasakamoto.herokuapp.com/api/todos', item)
        .catch((err) => {
          console.log('Delete had an error: ', err)
        })
      this.isChanged = true
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
.todo-row {
  width: 100%;
}
</style>
