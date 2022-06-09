<template>
  <div class="ss" v-for="(id, index) in todos" :key="id.id">
    <button @click="deleteTodo(index)">delete</button>
    {{ id.subject }}
  </div>
</template>

<script setup>
// eslint-disable-next-line
const props = defineProps({
  todos: String
})

// eslint-disable-next-line
const emit = defineEmits(['deleteTodo, index'])
const deleteTodo = (index) => {
  emit('delete-Todo', index)
}

</script>

<style>

</style>
