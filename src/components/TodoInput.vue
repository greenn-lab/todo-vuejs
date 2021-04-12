<template>
  <form @submit.prevent="save()">
    <label><input v-model="todo"></label>
    <button>OK</button>
  </form>
</template>

<script>
export default {
  name: 'TodoInput',
  methods: {
    save() {
      this.$emit('add', this.todo)
      this.todo = ''
    }
  },
  data() {
    return {
      todo: ''
    }
  }
}
</script>

