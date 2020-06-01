<template>
  <div>
    <form @submit.prevent="addTodo" class="input-form">
      <input
        class="form-control todo-list-input"
        type="text"
        v-model="title"
        name="title"
        placeholder="What do u need to do today ?"
      />
      <input type="submit" value="Add" class="btn btn-primary" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        title: this.title,
        completed: false
      };
      this.$emit("add-todo", newTodo);

      this.title = "";
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}
.form-control {
  display: block;
  width: 100%;
  height: 3.5rem;
  padding: 0.875rem 1.375rem;
  font-size: 1rem;
  line-height: 1;
  color: #495057;
  background-color: #ffffff;
  background-clip: padding-box;
  border: 1px solid #ced4da;
  border-radius: 2px;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}
.btn-primary {
  margin-left: 15px;
  font-size: 1.5rem;
  font-weight: 700;
}
.input-form {
  padding-bottom: 7px;
}
</style>

