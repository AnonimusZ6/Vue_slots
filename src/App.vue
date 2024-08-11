<template>
  <div id="app">
    <div class="container">
      <TodoList>
      <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @remove="removeTodo"
      >
        {{ todo.text }}
      </TodoItem>
    </TodoList>
    <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Добавить новое дело" class="form-control"/>
    </div>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';
import TodoItem from './components/TodoItem.vue';

export default {
  name: 'App',
  components: {
    TodoList,
    TodoItem,
  },
  data() {
    return {
      newTodo: '',
      todos: [],
      nextId: 1, // Для уникальных идентификаторов
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({
          id: this.nextId++,
          text: this.newTodo,
          completed: false,
        });
        this.newTodo = '';
      }
    },
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
  },
};
</script>

<style>
#app {
  max-width: 400px;
  margin: auto;
}
input {
  margin-top: 16px;
  padding: 8px;
}
</style>