<template>
    <div class="todo-list">
      <h2>Список дел</h2>
      <ul>
        <div class="card">
            <div class="card-body" style="gap: 10px">
                <slot></slot>
            </div>
        </div>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'TodoList',
  };
  </script>
  