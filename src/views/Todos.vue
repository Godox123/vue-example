<template>
  <div id="app">
    <router-link to="/">Home</router-link>

    <addTodo @add-todo="AddTodo" />
    <Loader v-if="loading" />
    <Todo
      v-else-if="todos.length"
      @remove-todo="removeTodo"
      v-bind:todos="todos"
    />
    <p v-else>Ничего нет</p>
  </div>
</template>

<script>
import Todo from '@/components/Todo';
import addTodo from '@/components/addTodo';
import Loader from '@/components/loader';
export default {
  name: 'App',
  components: { Todo, addTodo, Loader },
  data() {
    return {
      todos: [],
      loading: true
    };
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos')
      .then(response => response.json())
      .then(json => {
        this.todos = json;
        this.loading = false;
      });
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id);
    },
    AddTodo(todo) {
      this.todos.push(todo);
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
