<template>
    <li :class="{ completed: isCompleted }" class="d-flex" style="gap: 10px">
      <input type="checkbox" v-model="isCompleted" />
      <slot></slot>
      <button @click="removeItem" class="btn btn-danger">Удалить</button>
    </li>
  </template>
  
  <script>
  export default {
    name: 'TodoItem',
    props: {
      todo: {
        type: Object,
        required: true,
      },
    },
    data() {
      return {
        isCompleted: this.todo.completed,
      };
    },
    methods: {
      removeItem() {
        this.$emit('remove', this.todo.id);
      },
    },
  };
  </script>
  
  <style scoped>
  li {
    list-style-type: none;
    display: flex;
    align-items: center;
  }
  .completed {
    text-decoration: line-through;
  }
  button {
    margin-left: auto;
  }
  </style>