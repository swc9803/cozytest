<template>
  <div class="dd">
    <form @submit.prevent="onSubmit">
      <div>
        <input type="text" v-model="todo" placeholder="write todo">
        <button type="submit">add</button>
      </div>
    </form>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  setup (props, { emit }) {
    const todo = ref('')

    const onSubmit = () => {
      emit('addTodo', {
        id: Date.now(),
        subject: todo.value
      })
    }

    return {
      todo,
      onSubmit
    }
  }
}
</script>

<style lang="scss" scoped>
.dd {
  max-width: 80%;
}
.ss {
  width: 100%;
}
</style>
