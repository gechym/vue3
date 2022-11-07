<template>
  <div>
    <input type='text' @keyup.enter="handleAddTodo" placeholder='add todo...' v-model='value'>
    <button @click="handleAddTodo">add
    </button>
  </div>
</template>

<script lang='ts'>
import {ref, defineComponent} from 'vue'

export default defineComponent({
  name: 'AddTodoInput',
  setup(props, {emit}) {
    const value = ref('')
    const handleAddTodo = () => {
      emit('addTodo', {
        id: Math.floor(Math.random() * 1000),
        text: value.value,
        completed: false
      })
      value.value = ''
    }
    return {
      value,
      handleAddTodo
    }
  }
})
</script>
