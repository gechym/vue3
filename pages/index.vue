<template>
  <div>
    <div v-if="messages && messages.length">
      <p v-for="message in messages" :key="message.text">
        {{ message.text }}
      </p>
    </div>
    <div v-else>
      <p>No messages</p>
    </div>
  </div>
</template>

<script lang='ts'>
import { defineComponent, ref } from 'vue'

export default defineComponent({
  data() {
    return {
      messages : []
    }
  },
  async mounted() {
      const res: any = await (await fetch('http://localhost:8080/message')).json()
      const {data} = res
      this.messages = data
    setInterval(async () => {
        const res: any = await (await fetch('http://localhost:8080/message')).json()
        const {data} = res
        this.messages = data
    }, 5000)
  }
})
</script>
