<template>
  <div>
    <header-component :count='count' @increment='handleIncrement'/>
    <add-todo-input @addTodo="handleAddTodo"/>
    <item-component
      v-for='todo in todos'
      :key='todo.id'
      :todoProps='todo'
      @toggleTodoCompleted='handleToggleTodoComplete'
      @deleteTodo='handleDeleteTodo'
    />

  </div>
</template>

<script lang='ts'>
import { defineComponent, ref } from 'vue'
import HeaderComponent from '~/components/HeaderComponent.vue'
import ItemComponent from '~/components/ItemComponent.vue'
import AddTodoInput from '~/components/AddTodoInput.vue'

export default defineComponent({
  name: 'MainComponent',
  components: {
    HeaderComponent, ItemComponent,AddTodoInput
  },
  setup() {
    const count = ref(0)
    const todos = ref([
      { id: 1, text: 'Todo 1', completed: true },
      { id: 2, text: 'Todo 2', completed: false }
    ])

    const handleIncrement = () => {
      count.value++
    }

    const handleToggleTodoComplete = (id : number) =>  {
      todos.value = todos.value.map((todo) => {
        if(todo.id === id){
          todo.completed = !todo.completed
          return todo
        }
        return todo
      })
    }

    const handleDeleteTodo = (id : number) => {
      todos.value = todos.value.filter((todo) => todo.id !== id)
    }

    const handleAddTodo = (todo : {id: number, text: string, completed: boolean,}) => {
      todos.value.push(todo)
    }


    return {
      count,
      todos,
      handleAddTodo,
      handleToggleTodoComplete,
      handleIncrement,
      handleDeleteTodo,
    }
  }
})

</script>
