<template>
  <ul>
    <li v-for="todo in todos.slice().reverse()" :key="todo.id" class="todo-item">
      <p class="todo-item__value">{{ todo.title }}</p>
      <button class="todo-item__remove" type="button" @click="remove(todo.id)">&times;</button>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'TodoList',
  props: ['todos'],
  methods: {
    remove(id) {
      this.$emit('remove', id)
    }
  }
}
</script>

<style scoped>
  .todo-item {
    display: flex;
  }

  .todo-item__value {
    margin: 0 1rem;
    order: 1;
  }
</style>
