<template>
  <div>
    <p
      :class="[todoProps.completed ? 'text-blue-700' : '']"
    >
    {{todoProps.text}}
    </p>
    <input
      type='checkbox'
      :checked='todoProps.completed'
      @change='toggleTodoCompleted()'>
    <button @click='deleteTodo()'>Xóa</button>
  </div>

</template>

<script lang='ts'>
  import {defineComponent} from 'vue'

  export default defineComponent({
    name : "ItemComponent",
    props : ['todoProps'],
    // eslint-disable-next-line vue/no-setup-props-destructure
    setup : ({ todoProps : {id}} : any,ctx) => {
      const toggleTodoCompleted = () => {
        ctx.emit('toggleTodoCompleted',id)
      }

      const deleteTodo = () => {
        ctx.emit('deleteTodo',id)
      }
      return {
        toggleTodoCompleted,deleteTodo
      }
    }
  })
</script>
