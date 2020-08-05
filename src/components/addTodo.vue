<template>
  <form @submit.prevent="onSubmit()">
    <input type="text" v-model="title" />
    <button type="submit">create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ''
    };
  },
  methods: {
    onSubmit() {
      let newTodo;
      if (this.title.trim()) {
        newTodo = {
          id: Date.now(),
          title: this.title,
          complited: false
        };
      }
      this.$emit('add-todo', newTodo);
      this.title = '';
    }
  }
};
</script>

<style scoped>
input {
  width: 15vw;
  height: 5vh;
  margin: 3vw;
  font-size: 2vh;
  border: none;
  background: linear-gradient(#444444, #5b5b5d, #a0a0a1, #e4e4e6);
  border-radius: 0.4vh;
  color: black;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
button {
  border: none;
  width: 5vw;
  height: 4vh;
  font-size: 2vh;
  background: linear-gradient(#444444, #5b5b5d, #a0a0a1, #e4e4e6);
  border-radius: 0.4vh;
  color: black;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
</style>
