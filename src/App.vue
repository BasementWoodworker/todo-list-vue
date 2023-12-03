<template>
  <div>
    <AddTodoForm @add="addTodo" />
    <Todo v-for="todo in todos" :key="todo.id" :todo="todo" @delete="deleteTodo" @saveEdited="saveEdited" />
  </div>
</template>

<script>
  import "./index.css";
  import Todo from './components/Todo.vue';
  import AddTodoForm from './components/AddTodoForm.vue';
  export default {
    components: {
      Todo: Todo,
      AddTodoForm: AddTodoForm
    },
    data() {
      return {
        todos: []
      }
    },
    methods: {
      addTodo(text) {
        const newTodo = {
          id: Date.now(),
          text
        }
        this.todos.push(newTodo);
        this.input = "";
      },
      deleteTodo(id) {
        this.todos = this.todos.filter(todo => todo.id !== id);
      },
      saveEdited(editedTodo) {
        const todoIndex = this.todos.findIndex(todo => todo.id === editedTodo.id);
        this.todos[todoIndex] = editedTodo;
      }
    }
  }
</script>
