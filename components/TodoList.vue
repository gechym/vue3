<template>
  <div>
    <p v-for="todo in listTodo" :key='todo.title'>{{todo.title}} : {{todo.description}}</p>
  </div>
</template>

<script lang='ts'>
import { computed, PropType } from 'vue'
import { OrderBy, Todo } from '~/Type/type'

export default {
  name: 'TodoList',

  props : {
    todos : {
      required : true,
      type : Array as PropType<Todo[]>,
    },
    orderBy : {
      required : true,
      type : String as PropType<OrderBy>,
    },
  },

  setup(props : {todos : Todo[], orderBy : OrderBy}, context : any) {

    const listTodo = computed(() => {
      return [...props.todos].sort((a, b) => {
        if (a[props.orderBy] > b[props.orderBy]) {
          return 1
        } else if (a[props.orderBy] < b[props.orderBy]) {
          return -1
        } else {
          return 0
        }
      })
    })


    return {
      listTodo
    }
  },
}
</script>
