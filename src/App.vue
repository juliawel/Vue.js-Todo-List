<script setup>
import {ref, onMounted, computed, watch} from 'vue'

const todos = ref([])
const name = ref('')

const input_content = ref('')
const input_category = ref(null)

const addTodo = () => {}

// show the latest created at front
const todos_asc = computed(() => todos.value.sort((a,b) => {
  return b.createdAt - a.createdAt
}))

watch(name, (newVal) => {
  localStorage.setItem('name', newVal)
})

onMounted(() => {
	name.value = localStorage.getItem('name') || ''
})
</script>

<template>
  <main class="app">

    <section class="greeting">
      <h2 class="title">
        What's up, <input type="text" placeholder="name here" 
        v-model="name">
      </h2>
    </section>

    <section class="create-todo">
      <h3>CREATE A TODO</h3>

      <form @submit.prevent="addTodo"></form>
    </section>

  </main>
</template>


