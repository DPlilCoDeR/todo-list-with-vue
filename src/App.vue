<template>
  <div id="app">
    <Header />
    <addTodo v-on:add-todo="addTodo" />
    <Todo v-bind:todo="todo" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/layouts/header.vue';
import Todo from './components/todo.vue';
import addTodo from './components/addTodo.vue';

export default {
  name: 'app',
  components: {
    Todo,
    Header,
    addTodo,
  },
  data() {
    return {
      todo: [
        {
          id: 1,
          title: 'Todo One',
          completed: false,
        },
        {
          id: 2,
          title: 'Todo Two',
          completed: false,
        },
        {
          id: 3,
          title: 'Todo Three',
          completed: false,
        },
      ],
    };
  },
  methods: {
    deleteTodo(id) {
      this.todo = this.todo.filter(todo => todo.id !== id);
    },

    addTodo(newTodo) {
      this.todo = [...this.todo, newTodo];
    },
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res => this.todo = res.data)
      .catch(err => console.log(err));
  },
};
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0%;
    padding: 0%;
  }

  body {
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', Arial, sans-serif;
    line-height: 1.4;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover{
    background: red;
  }
</style>
