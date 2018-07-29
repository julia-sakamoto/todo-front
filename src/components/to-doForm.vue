<template>
  <div id="todo-form">
    <div class="container input-group form">
        <input type="text" class="form-control" id="input" placeholder="宿題を終わらせること" v-model="title"/>
        <button @click="addToApi" type="button" id="enterBtn" class="btn input-group-append">リストに追加</button>
    </div>
  </div>
</template>

<script>
const axios = require('axios')

export default {
  name: 'ToDoForm',
  data () {
    return {
      title: 'temp'
    }
  },
  methods: {
    addToApi () {
      axios.post('https://todo-server-juliasakamoto.herokuapp.com/', {
        Title: this.title,
        headers: {
          'Access-Control-Allow-Origin': '*'
        }
      })
        .then((res) => {
          console.log(res, 'Todo added')
        })
        .catch((err) => {
          console.log(err, 'Todo failed to add')
        })
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
