<template>
    <footer class="w-full">
      <section class="flex w-full justify-between space-x-4">
        <p class="font-light text-slate-400">
          {{ undoneTodosCount ? `${undoneTodosCount} todos left` : 'No todos' }}
        </p>
        <ul class="flex justify-center space-x-4">
          <li v-for="(footerLink, index) in footerLinks" :key="index">
            <a
              :href="footerLink.url"
              :class="{
                'rounded-sm border border-purple-500 p-2 text-purple-900': url == footerLink.url
              }"
            >
              {{ footerLink.label }}
            </a>
          </li>
        </ul>
        <a
          :href="'/todos'"
          @click.prevent="clearCompleted"
          class="font-light decoration-purple-800 hover:underline"
        >
          Clear completed
        </a>
      </section>
    </footer>
  </template>
  
  <script>
import { usePage } from '@inertiajs/inertia-vue3'
import { Inertia } from '@inertiajs/inertia'

  
  export default {
    props: {
      undoneTodosCount: {
        type: Number,
        required: true
      }
    },
    data() {
      return {
        url: null,
        footerLinks: [
          {
            label: 'All',
            url: '/'
          },
          {
            label: 'Undone',
            url: '/?completed=false'
          },
          {
            label: 'Done',
            url: '/?completed=true'
          }
        ]
      }
    },
    created() {
      this.url = usePage().url
    },
    methods: {
      clearCompleted() {
        Inertia.delete('/todos')
      }
    }
  }
  </script>
  