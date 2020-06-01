<template>
  <div id='app' class="container main-container">
    <AddTodo v-on:add-todo='addTodo' />
    <Todos v-bind:todos='todos' v-on:del-todo='deleteTodo' />
  </div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Todos,

    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      axios.delete('https://jsonplaceholder.typicode.com/todos')
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    AddTodo(newTodo){
      const {title, completed} = newTodo;
       axios.post('https://jsonplaceholder.typicode.com/todos',{
         title,
         completed
       })
       .then(res =>this.todos = [...this.todos, res.data])
       .catch(err => console.log(err))
      this.todos = [...this.todos, newTodo];
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  line-height: 1.4;
}
.main-container {
  padding-top: 15px;
}

.custom-button {
  display: inline-block;
  border: none;
  background: darkgrey;
  color: white;
  padding: 7px 20px;
  cursor: pointer;
}
.custom-button:hover {
  background: darkslategray;
}
</style>
