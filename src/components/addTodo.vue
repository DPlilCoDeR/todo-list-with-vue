<template>
  <div>
      <form @submit="addTodo">
          <input type="text" v-model="title" name="title" placeholder="Añade una tarea">
          <input type="submit" value="Submit" class="btn">
      </form>
  </div>
</template>

<script>
import { uuid } from 'uuidv4';

export default {
  name: 'addTodo',
  data() {
    return {
      title: '',
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false,
      };

      this.$emit('add-todo', newTodo);

      this.title = '';
    },
  },
};
</script>

<style scoped>
  form {
    display: flex;
  }

  input[type ="text"]{
    flex: 10;
    padding: 5px;
  }

  input[type ='submit']{
    flex: 2;
  }
</style>
