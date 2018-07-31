<template>
  <div id="todo-form">
    <div class="container input-group form">
      <input type="text" class="form-control" id="input" placeholder="宿題を終わらせること" v-model="title" @keydown.enter="addToApi" />
      <button @click="addToApi" type="button" id="enterBtn" class="btn input-group-append">リストに追加</button><br>
    </div>
    <p v-if="isAdded">リストが更新されました！F5を押してください。</p><br>
  </div>
</template>

<script>
const axios = require('axios')

export default {
  name: 'ToDoForm',
  data () {
    return {
      title: '',
      isAdded: false
    }
  },
  methods: {
    addToApi () {
      axios.post('https://todo-server-juliasakamoto.herokuapp.com/api/todos', {
        Title: this.title
      })
        .then((res) => {
          console.log('Todo added', res)
        })
        .catch((err) => {
          console.log('Todo failed to add', err)
        })

      this.isAdded = true
    }
  }
}
</script>

<style>
#input {
  width: 80%;
}
#enterBtn {
  float: right;
  width: 20%;
}
.form {
  width: 50%;
}
</style>
