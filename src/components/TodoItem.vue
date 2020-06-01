<template>
  <div class="todo-items" v-bind:class="{'complete':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" />
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="delete-button">X</button>
    </p>
  </div>
</template>
<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
      markComplete(){
          this.todo.completed = !this.todo.completed
      }
  }
};
</script>

<style  scoped>
.todo-items {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.complete {
  text-decoration: line-through;
}
.delete-button {
  background: #c0392b;
  color: white;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>