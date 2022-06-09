<template>
  <div>
    {{ name.id }}
    {{ name.test }}
  </div>
  <input :type="type" :value="name.test">
  <button @click="update">Click</button>
</template>

<script setup>
import { reactive, ref } from 'vue'
// 객체는 reactive
const name = reactive({
  id: 1,
  test: 'hi'
})

const type = ref('text')

const update = () => {
  name.test = 'sung woo'
  type.value = 'number'
}
</script>

<style lang="scss" scoped>

</style>
