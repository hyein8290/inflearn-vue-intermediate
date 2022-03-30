<template>
  <div class="inputBox">
      <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
      <span class="addContainer" v-on:click="addTodo">
          <i class="fas fa-plus addBtn"></i>
      </span>
  </div>
</template>

<script>
export default {
    data: function() {
        return {
            newTodoItem: ""
        }
    },
    methods: {
        addTodo: function() {
            console.log(this.newTodoItem);
            this.clearInput();
        },
        clearInput: function() {
            this.newTodoItem = '';
        }
    }
}
</script>

<style scoped>

</style>