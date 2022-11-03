<template>
  <div>
    <h1>{{ x }} {{ y }}</h1>
    <div class='flex gap-0.5'>
      <div @mouseover='onMouseOver($event)' class='w-96 h-96 bg-blue-600'>
        Mouse over
      </div>
      <div @dblclick='onMouseOver($event)' class='w-96 h-96 bg-blue-600'>
        Mouse double click
      </div>
      <div @click='onMouseOver' class='w-96 h-96 bg-blue-600'>
        Mouse click
      </div>
      <div @mousemove='onMouseMove($event)' class='w-96 h-96 bg-blue-600'>
        Mouse move
      </div>
    </div>
  </div>
</template>

<script lang='ts'>
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'CardEvent',
  setup() {
    const x = ref<number>(0)
    const y = ref<number>(0)
    return {
      x,
      y
    }
  },
  methods: {
    onMouseMove(e: MouseEvent) {
      console.log(e)
      this.x = e.offsetX
      this.y = e.offsetY
    },
    onMouseOver(e: MouseEvent) {
      console.log(e)
    }
  }
})
</script>

