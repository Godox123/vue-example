<template>
  <div>
    <ul>
      <TodoItem
        v-on:remove-todo="removeTodo"
        v-for="(todo, i) in todos"
        v-bind:index="i"
        :key="todo.id"
        v-bind:todo="todo"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem';
export default {
  name: 'Todo',
  props: ['todos'],
  components: {
    TodoItem
  },
  methods: {
    removeTodo(id) {
      this.$emit('remove-todo', id);
    }
  }
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>
