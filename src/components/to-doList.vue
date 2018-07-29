<template>
  <div id="to-do-list">
      <ul class="container list">
        <li>{{status}} {{item}} - {{date}}</li>
      </ul>
  </div>
</template>

<script>
export default {
  name: 'ToDoList',
  methods: {
    status () {
      return 'n'
    },
    item () {
      return 'n'
    },
    date () {
      return 'n'
    }
  }
}
</script>

<style>
.list {
  list-style: none;
  padding: 2em;
}
</style>
