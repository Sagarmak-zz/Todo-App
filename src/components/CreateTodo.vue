<template lang="html">
  <div class="add-todo">

    <div class='ui basic content center aligned segment'>
      <button class='ui basic button icon' @click="isCreating = true" v-show="!isCreating">
        <i class='plus icon'></i>
      </button>
      <div class='ui centered card' v-show="isCreating">
        <div class='content'>
          <h1 class="ui header">
				<span>Add a Todo</span>
			</h1>
          <div class='ui form'>
            <div class='field'>
              <label>Title</label>
              <input v-model="titleText" type='text'>
            </div>
            <div class='field'>
              <label>Project</label>
              <input v-model="projectText" type='text'>
            </div>
            <div class='ui two button attached buttons'>
              <button class='ui basic blue button' @click="sendForm">
                Create
              </button>
              <button class='ui basic red button' @click="isCreating = false">
                Cancel
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'add-todo',

  data() {
    return {
      titleText: '',
      projectText: '',
      isCreating: false,
    }
  },

  methods: {
    sendForm() {
      if (this.titleText.length > 0 && this.projectText.length > 0) {
        this.$emit('create-todo', {
          title: this.titleText,
          project: this.projectText,
          done: false
        });
        this.isCreating = false;
      }
      else {
        //show error
        console.log('Error');
      }
    }
  }
}
</script>

<style>
.add-todo {}
</style>
