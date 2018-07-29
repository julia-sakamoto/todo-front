<template>
  <div id="to-do-Form">
    <div class="container input-group form">
        <input type="text" class="form-control" id="input" placeholder="宿題を終わらせること" v-model="title"/>
        <button @click="addToApi" type="button" id="enterBtn" class="btn input-group-append">リストに追加</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ToDoForm',
  data () {
    return {
      title: ''
    }
  },
  methods: {
    addToApi () {
      console.log('nothing yet')
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
