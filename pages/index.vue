<template>
  <div>
    <p id='counter'>{{ count }}</p>
    <br />
    <button @click='increment(count + 1)'>+1 (click me)</button>
    <br />
    <div v-if='isShow'>
      <button @click='changeOrderBy("title")'>order by title</button>
      <br />
      <button @click='changeOrderBy("description")'>order by description</button>
      <p>{{ orderBy }}</p>
      <TodoList :todos='todos' :order-by='orderBy' />
    </div>
    <CardEvent />
  </div>
</template>

<script lang='ts'>
import { defineComponent, ref } from 'vue'
import TodoList from '~/components/TodoList.vue'
import CardEvent from '~/components/CardEvent.vue'
import { OrderBy, Todo } from '~/Type/type'

export default defineComponent({
  components: { TodoList, CardEvent },
  data() {
    return {
      count: 0
    }
  },
  setup() {
    const todos = ref<Todo[]>([
      {
        title: 'title1',
        description: 'description1'
      },
      {
        title: ' title3',
        description: ' asdasd description2'
      },
      {
        title: '123 ádasd itle2',
        description: 'description123'
      }
    ])
    const orderBy = ref<OrderBy>('title')
    const isShow = ref<boolean>(false)
    return {
      // count,
      todos,
      orderBy,
      isShow
    }
  },
  methods: {
    increment(value: number) {
      this.count = value
      this.isShow = !this.isShow
    },
    changeOrderBy(value: OrderBy) {
      this.orderBy = value
    }
  }
})
</script>
