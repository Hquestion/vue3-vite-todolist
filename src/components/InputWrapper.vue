<template>
<div class="input-wrapper">
  <input type="text" v-model="key" @keyup.enter="handleEnter">
</div>
</template>

<script setup="props, {emit}" lang="ts">
import { ref } from 'vue'
export const key = ref('')

export function handleEnter() {
  if (!key.value || !key.value.trim()) return
  emit('add', key.value)
  key.value = ''
}

</script>

<style lang="scss" scoped>
.input-wrapper {
  input {
    border: 1px solid #f80;
    width: 400px;
    height: 40px;
    line-height: 40px;
    background: #fff;
    text-indent: 10px;
    color: #f80;
    font-size: 24px;
    outline: none;
    &:focus, &:active {
      border: 1px solid #f80;
    }
  }
}
</style>