<template>
  <div id="app">
    <h1>Todo List</h1>
    <ul>
      <li v-for='todo in todos' v-bind:key="todo">{{todo}}</li>
    </ul>
    <form v-on:submit.prevent="addTodo">
      <input v-model="todoText" placeholder="input your new Todo">
      <input type="submit" value="Add Todo">
    </form>
    <!-- <img alt="Vue logo" src="https://vuejs.org/images/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data: function() {
    return {
      todos: [],
      todoText: ''
    }
  },
  methods: {
    addTodo: function () {
      this.todos = [...this.todos, this.todoText]
      localStorage.setItem('todos', JSON.stringify(this.todos))
    }
  },
  mounted: function() {
    const existingTodos = localStorage.getItem('todos')
    this.todos = JSON.parse(existingTodos) || []
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
