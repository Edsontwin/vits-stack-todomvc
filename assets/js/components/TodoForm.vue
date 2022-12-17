<template>
    <form class="w-full" @submit.prevent="handleSubmit">
      <input
        autoFocus
        class="w-full border-none text-xl text-gray-900 caret-purple-500 placeholder:text-gray-400/60 focus:outline-none"
        type="text"
        name="name"
        v-model="newTodo"
        placeholder="What do you want to get done?"
      />
    </form>
  </template>
  
  <script>
  import { Inertia } from '@inertiajs/inertia'
  
  export default {
    name: 'TodoForm',
    data() {
      return {
        newTodo: ''
      }
    },
    methods: {
      handleSubmit() {
        Inertia.post('/todos', { name: this.newTodo })
        this.newTodo = ''
      }
    }
  }
  </script>
  