<script setup>
  import { Inertia } from '@inertiajs/inertia'
  

  const props = defineProps({
    todos: Array,
  })

  function updateTodo(id){
    Inertia.put(`/todos/${id}`)
  }
  </script>
<template>
    <ul class="flex flex-col items-start justify-start space-y-4">
      <li v-for="(todo, index) in todos" :key="index" class="group flex w-full items-center space-x-2 text-xl">
        <input
          type="checkbox"
          v-model="todo.completed"
          class="h-6 w-6 accent-purple-500"
          @change="updateTodo(todo.id)"
        />
        <label
          class="flex-1"
          :class="{ 'text-gray-400 line-through': todo.completed, 'text-gray-600': !todo.completed }"
        >
          {{ todo.name }}
        </label>
        <Link
              :href="(`/todos/${todo.id}`)"
              method="delete"
              as="button"
              title="Remove todo"
              className="justify-self-end text-lg text-gray-400 opacity-0 hover:text-gray-600 group-hover:opacity-100"
            >
              &#10005;
            </Link>
      </li>

    </ul>
  </template>
  
  
  