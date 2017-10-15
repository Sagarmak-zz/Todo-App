<template lang="html">
  <div class="todo">

    <div class="ui cards">

      <div class="card ui centered card">
        <div class="content">
          <div class="header">
            {{todo.title}}
          </div>
          <!-- <div class="meta">
          Friends of Veronika
        </div> -->
        <div class="description">
          {{todo.project}}
        </div>
        <div class='extra content'>
          <span @click="isEditing = true" class='right floated edit icon'>
            <i class='edit icon'></i>
          </span>
          <span @click="deleteTodo(todo)" class='right floated trash icon'>
            <i class='trash icon'></i>
          </span>
        </div>
      </div>

      <div class="content" v-show="isEditing">
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input type='text' v-model="todo.title" >
          </div>
          <div class='field'>
            <label>Project</label>
            <input type='text' v-model="todo.project" >
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' @click="isEditing = false">
              Close X
            </button>
          </div>
        </div>
      </div>

      <div class='ui bottom attached green basic button' v-show="todo.done">
        Completed
      </div>
      <div class='ui bottom attached red basic button' v-show="!todo.done" @click="completeTodo(todo)">
        Pending
      </div>
    </div>

  </div>

</div>
</template>

<script>
export default {
  name: 'todo',

  props: ['todo', 'index'],

  data() {
    return {
      isEditing: false,
    }
  },

  methods: {
    deleteTodo(todo) {
      this.$emit('delete-todo', todo);
    },
    completeTodo(todo) {
      this.$emit('complete-todo', todo);
    }
  }

}
</script>

<style>
.todo {
  padding-bottom: 1rem;
}
</style>
