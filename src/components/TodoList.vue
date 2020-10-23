<template>
<div class="todo-list">
  <div
      class="todo-item"
      v-for="(item, index) in renderList"
      :key="index"
      :class="{'is-finish': item.status === 1}"
  >
    <span>
      {{ item.name }}
    </span>
    <div class="actions">
      <i @click="finish(index)">√</i>
      <i @click="deleteItem(index)">X</i>
    </div>
  </div>
</div>
</template>

<script lang="ts" setup="props, {emit}">
import { computed } from 'vue'
declare const props: {
  list: Array<string>
}

export const renderList = computed(() => (props.list || []).sort((a, b) => a.status - b.status))

export const deleteItem = (index) => {
  emit('del', index)
}

export const finish = (index) => {
  emit('finish', index)
}

</script>

<style lang="scss" scoped>
.todo-list {
  margin: 20px auto 0;
  width: 400px;
  min-height: 100px;
  .todo-item {
    width: 100%;
    height: 35px;
    line-height: 35px;
    background: azure;
    padding: 10px;
    box-sizing: border-box;
    display: flex;
    align-items: center;
    justify-content: space-between;
    text-align: left;

    span {
      flex:1;
    }
    i {
      display: inline-block;
      width: 30px;
      font-size: 20px;
      color: #e24;
      cursor: pointer;
      font-style: normal;
      opacity: 0.2;
      transition: opacity ease .2s;
      text-align: center;
    }
    & + .todo-item {
      margin-top: 10px;
    }
    &:hover {
      i {
        opacity: 1;
      }
    }
    &.is-finish {
      text-decoration: line-through;
      opacity: 0.5;
      pointer-events: none;
    }
  }
}
</style>