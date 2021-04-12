<template>
  <div>
    <todo-input @add="addTodo"/>
    <todo-list :todos="todos" @remove="removeTodo"/>
  </div>
</template>

<script>
import TodoInput from '@/components/TodoInput'
import TodoList from "@/components/TodoList";
import v4 from "uuid";
import axios from "axios";

export default {
  name: 'App',
  components: {
    TodoInput, TodoList
  },
  methods: {
    addTodo(value) {
      this.todos.push({
        id: v4(),
        title: value,
        completed: false
      })
    },
    removeTodo(id) {
      this.todos.splice(this.todos.findIndex(i => i.id === id), 1)
    }
  },
  data() {
    return {
      todos: []
    }
  },
  mounted() {
    axios.get('https://jsonplaceholder.typicode.com/todos')
        .then(function(res) {
          this.todos = res.data
        }.bind(this))
  }
}
</script>
