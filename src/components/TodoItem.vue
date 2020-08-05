<template>
  <li>
    <span v-bind:class="{ done: todo.completed }">
      <input type="checkbox" v-on:change="todo.completed = !todo.completed" />
      <strong>{{ index + 1 }}</strong>
      {{ todo.title }}
    </span>
    <button class="delete-button" v-on:click="$emit('remove-todo', todo.id)">
      delete
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  }
};
</script>

<style scoped>
li {
  border: 1px solid rgb(50, 52, 75);
  display: flex;
  justify-content: space-between;
  padding: 2vh 2vw;
  margin-bottom: 1vh;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
input {
  margin-right: 1vw;
}
.delete-button {
  background: rgb(31, 137, 141);
  cursor: pointer;
  color: black;
  height: 4vh;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-weight: bold;
  border-radius: 1vh;
}
.done {
  text-decoration: line-through;
}
</style>
