<template>
  <div>
    <input type='text' placeholder='add todo...' v-model='value' @input='check'>
    <button>add</button>
  </div>
</template>

<script lang='ts'>
import { ref, defineComponent } from 'vue'

export default defineComponent({
  name: 'AddTodoInput',
  setup() {
    const value = ref('')
    return {
      value,
      check: () => {
        console.log(value.value)
      }
    }
  }
})
</script>
