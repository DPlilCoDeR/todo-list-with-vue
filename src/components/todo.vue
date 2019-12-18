<template>
<div>
    <div v-bind:key="todo.id" v-for="todo in todo">
      <todoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
</div>

</template>

<script>
import todoItem from './todoItem.vue';

export default {
  name: 'todo',
  components: {
    todoItem,
  },
  props: ['todo'],
};
</script>

<style scoped>

</style>
