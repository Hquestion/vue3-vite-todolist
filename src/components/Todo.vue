<template>
  <div class="todo">
    <InputWrapper @add="handleAdd" />
    <TodoList :list="list" @del="handleDel" @finish="handleFinish" />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
export { default as InputWrapper } from './InputWrapper.vue'
export { default as TodoList } from './TodoList.vue'

export const list = ref([])

export const handleAdd = (item) => {
  list.value.push({name: item, status: 0})
}

export const handleDel = (index) => {
  list.value.splice(index, 1)
}

export const handleFinish = (index) => {
  list.value[index].status = 1
}

</script>

<style lang="scss" scoped>
.todo {
  width: 800px;
  margin: 0 auto;
  background: #eed;
  padding: 40px;
}
</style>