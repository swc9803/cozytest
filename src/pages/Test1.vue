<template>
  <div class="dd">
    <h2>to-do-list</h2>

    <input type="text" v-model="searchText" placeholder="search text">

    <TodoForm @addTodo="addTodo" />
    <TodoList @delete-Todo="deleteTodo" :todos="filteredTodos" />
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import TodoForm from '@/components/TodoForm.vue'
import TodoList from '@/components/TodoList.vue'
import axios from 'axios'
const todos = ref([])

const getTodo = async () => {
  // json-server --watch db.json --port 3000
  const res = await axios.get('http://localhost:3000/todos')
  todos.value = res.data
}
getTodo()

const addTodo = async (todo) => {
  try {
    const res = await axios.post('http://localhost:3000/todos', {
      subject: todo.subject
    })
    todos.value.push(res.data)
  } catch (err) {
    console.log(err)
  }
}

const deleteTodo = (index) => {
  todos.value.splice(index, 1)
}

const searchText = ref('')
const filteredTodos = computed(() => {
  if (searchText.value) {
    return todos.value.filter(todo => {
      return todo.subject.includes(searchText.value)
    })
  }
  return todos.value
})
</script>

<style lang="scss" scoped>
.dd {
  max-width: 80%;
}
.ss {
  width: 100%;
}
</style>
