<template>
  <main class="mx-auto mt-10 flex h-screen min-h-screen w-full flex-col space-y-8 px-4 text-gray-700 sm:w-2/6">
    <h1 class="text-center text-5xl text-purple-700">todos</h1>
    <TodoForm />
    <TodoList :todos="todos" />
    <TodoFooter :undoneTodosCount="undoneTodosCount" />
  </main>
  <footer class="flex justify-center space-x-4">
    <p>Built on the RITS Stack</p>
    <p>
      <a
        :href="githubUrl"
        target="_blank"
        class="text-purple-800 underline"
      >
        View the source
      </a>
    </p>
  </footer>
</template>

<script>
import TodoFooter from '@/components/TodoFooter'
import TodoList from '@/components/TodoList'
import TodoForm from '@/components/TodoForm'

export default {
  name: 'Index',
  components: {
    TodoForm,
    TodoList,
    TodoFooter
  },
  props: {
    todos: {
      type: Array,
      required: true
    },
    undoneTodosCount: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      githubUrl: 'https://github.com/sailscastshq/rits-stack-todomvc'
    }
  }
}
</script>
