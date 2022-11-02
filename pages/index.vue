<template>
  <div>
    <p>{{ count }}</p>
    <br/>
    <button @click='increment(count + 1)'>+1 (click me)</button>
    <br/>
    <button @click='changeOrderBy("title")'>order by title</button>
    <br/>
    <button @click='changeOrderBy("description")'>order by description</button>
    <p>{{orderBy}}</p>
    <TodoList :todos='todos' :order-by="orderBy"/>

  </div>
</template>

<script lang='ts'>
import { defineComponent, ref } from 'vue'
import TodoList from '~/components/TodoList.vue'
import { OrderBy, Todo } from '~/Type/type'

export default defineComponent({
  components: { TodoList },
  // data(){
  //   return {
  //     count: 0,
  //   }
  // },
  setup() {
    const count = ref(0)
    const todos = ref<Todo[]>([
      {
        title: 'title1',
        description: 'description1',
      },
      {
        title: ' title3',
        description: ' asdasd description2',
      },
      {
        title: '123 ádasd itle2',
        description: 'description123',
      },
    ])
    const orderBy = ref<OrderBy>('title')
    return {
      count,
      todos,
      orderBy,
    }
  },
  methods: {
    increment(value: number){
      this.count = value
    },
    changeOrderBy(value : OrderBy){
      this.orderBy = value
    },
  }
})
</script>
