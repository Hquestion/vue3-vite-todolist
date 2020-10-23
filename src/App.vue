<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <Todo />
</template>

<script lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import Todo from './components/Todo.vue'
import { ref, Ref, UnwrapRef, reactive, watch, toRefs, computed } from 'vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Todo
  },
  setup() {
    const hello: Ref<UnwrapRef<string>> = ref('hello')
    const input: Ref<UnwrapRef<string>> = ref('America')
    let president = ref('奥巴马')
    const age: UnwrapRef<{value: number}> = reactive({
      value: 70
    })



    watch(() => age.value, (val: number, oldval: number): void => {
      console.log(val)
      console.log(oldval)
      president.value = president.value + val
      console.log(president)
    })

    const doubleAge = computed(() => age.value * 2)

    return {
      hello,
      input,
      age,
      president,
      doubleAge
    }
  }
}
</script>
