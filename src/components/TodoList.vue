<template>
    <div class="container">
      <div class="row">
        <div class="col-12">
          <p class="display-3">Vue Todo List</p>
        </div>
      </div>
      <div class="row">
        <div class="col-12 col-lg-6 mb-2">
          <NewTodo @on-addtodo="addTodo($event)" />
        </div>
      </div>
      <div class="row">
        <div class="col-12 col-lg-6">
          <ul class="list-group">
            <TodoItem
              v-for="(todo, index) in todos"
              :key="index"
              :todoString="todo.todoString"
              :completed="todo.completed"
              @on-delete="deleteTodo(todo)"
              @on-toggle="toggleTodo(todo)"
              @on-edit="editTodo(todo, $event)"
            />
          </ul>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import TodoItem from "./Todo";
  import NewTodo from "./NewTodo";
  export default {
    components: {
      TodoItem,
      NewTodo
    },
    data() {
      return {
        todos: [
          { todoString: "Make Angular course", completed: false },
          { todoString: "Cook some food", completed: true },
          { todoString: "Make Youtube Videos", completed: true },
          { todoString: "Publish these videos", completed: false }
        ]
      };
    },
    methods: {
      addTodo(newTodo) {
        this.todos.push({
          todoString: newTodo,
          completed: false
        });
      },
      toggleTodo(todo) {
        todo.completed = !todo.completed;
      },
      editTodo(todo, newTodoString) {
        todo.todoString = newTodoString;
      },
      deleteTodo(deleteTodo) {
        this.todos = this.todos.filter(todo => todo !== deleteTodo);
      }
    }
  };
  </script>
  
  
  <style >
  </style>