<template lang="html">
  <div class="todo-list">

    <Todo
    v-for="todo,index in todos"
    :key="todo.id" :todo="todo"
    :index="index" @delete-todo="deleteTodo" 
    @complete-todo="completeTodo"></Todo>

  </div>
</template>

<script>
import Todo from '@/components/Todo';

export default {
  name: 'todo-list',

  props: ['todos'],

  components: {
    Todo
  },

  methods: {
      deleteTodo(todo) {
        const indexTodo = this.todos.indexOf(todo);
        this.todos.splice(indexTodo, 1);
      },
      completeTodo(todo) {
        const todoIndex = this.todos.indexOf(todo);
        this.todos[todoIndex].done = true;
      }
  }
}
</script>

<style>
.todo-list {

}
</style>
