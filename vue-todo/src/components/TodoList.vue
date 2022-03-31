<template>
  <div>
      <ul>
        <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item" class="shadow">
          <i class="checkBtn fas fa-check" v-bind:class="{checkBtnCompleted: todoItem.completed}" v-on:click="toggleComplete(todoItem)"></i>
          <span v-bind:class="{textCompleted: todoItem.completed}">{{ todoItem.item }}</span>
          <span class="removeBtn" v-on:click="removeTodo(todoItem, index)">
            <i class="fas fa-trash-alt"></i>
          </span>
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  props: ['propsdata'],
  // data: function() {
  //   return {
  //     todoItems: []
  //   }
  // },
  methods: {
    removeTodo: function(todoItem, index) {
      console.log(todoItem, index);
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    toggleComplete: function(todoItem) {
      todoItem.completed = !todoItem.completed;
      // 로컬 스토리지의 데이터를 갱신
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    }
  },
  // created: function() {
  //   if(localStorage.length > 0){
  //     for (var i = 0; i < localStorage.length; i++) {
  //       if (localStorage.key(i) !== 'loglevel:webpack-dev-server'){
  //         // console.log(JSON.parse(localStorage.getItem(localStorage.key(i))));
  //         // console.log(typeof localStorage.getItem(localStorage.key(i)));
  //         this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
  //         // this.todoItems.push(localStorage.key(i));
  //         // console.log(localStorage.key(i));
  //       }
  //     }
  //   }
  // }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
.checkBtn {
  line-height: 45px;
  /* color: black; */
  color: #62acde;
  margin-right: 5px;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}
.checkBtnCompleted {
  /* color: #62acde; */
  color: black;
}
.textCompleted {
  text-decoration: line-through;
}
</style>