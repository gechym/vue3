<template>
  <div class='text-blue-700 text-2xl font-black' @click='increment()'>
    TODOLIST asd {{count}}
  </div>
</template>

<script lang='ts'>
  import {defineComponent} from 'vue'
  export default defineComponent({
    name: 'HeaderComponent',
    props: ['count'],
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    setup(props,ctx){
      const increment = () => {
        ctx.emit('increment')
      }
      return {increment}
    }
  })
</script>
