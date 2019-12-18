<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <input type="checkbox" v-on:change="markComplete">
    <div>{{todo.title}}</div>
    <button @click="$emit('del-todo', todo.id)" class="del">x</button>
  </div>
</template>

<script>
export default {
  name: 'todoItem',
  props: ['todo'],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
  .todo-item{
      background: white;
      padding: 10px;
      border-bottom: 1px #cccccc dotted;
  }

  .is-complete{
    text-decoration: line-through;
  }

  .del{
    background: red;
    border: none;
    color: white;
    float: right;
    border-radius: 100%;
  }
</style>
