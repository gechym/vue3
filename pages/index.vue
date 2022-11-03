<script lang='ts'>

import { defineComponent } from 'vue'

export default defineComponent({
  data() {
    return {
      names: [
        {
          id: 1,
          name: 'John'
        },
        {
          id: 2,
          name: 'Jane'
        }
      ],
      prefix: '',
      pickId : -1,
      namePick : ''
    }
  },

  computed: {
    filteredNames() {
      return this.names.filter(item => item.name.includes(this.prefix))
    }
  },

  watch : {
    pickId (value) {
      console.log(value)
    }
  },

  methods: {
    addName() {
      this.names.push({
        id: Date.now(),
        name: this.namePick
      })
      this.handleClear()
    },
    deleteName(id: number) {
      this.names = this.names.filter(item => item.id !== id)
      this.handleClear()
    },
    updateName(id: number, name: string) {
      this.names = this.names.map(item => {
        if (item.id === id) {
          item.name = name
        }
        return item
      })
      this.handleClear()
    },
    handlePick(id: number, name: string) {
      this.pickId = id
      this.namePick = name
    },
    handleClear() {
      this.prefix = ''
      this.namePick = ''
      this.pickId = -1
    }
  }
})
</script>


<template>
  <div>
    <div><input v-model='prefix' placeholder='Filter prefix'></div>

    <select size='5'>
      <option v-for='name in filteredNames'  :key='name.id' @click='handlePick(name.id,name.name)'>
        {{ name.name }}
      </option>
    </select>

    <label>name: <input v-model='namePick'></label>

    <div class='buttons'>
      <button @click='addName()'>Create</button>
      <button @click='updateName(pickId,namePick)'>Update</button>
      <button @click='deleteName(pickId)' >Delete</button>
    </div>
  </div>
</template>


<style scoped>
* {
  font-size: inherit;
}

input {
  display: block;
  margin-bottom: 10px;
}

select {
  float: left;
  margin: 0 1em 1em 0;
  width: 14em;
}

.buttons {
  clear: both;
}

button + button {
  margin-left: 5px;
}
</style>
