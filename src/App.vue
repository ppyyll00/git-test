<template>
  <div>
    <h2>To-Do List</h2>
    <form
      @submit.prevent="onsubmit"
    >
      <input
        placeholder="to do list"
        v-model="todo"
      >
      <button
      type="submit"
      >
        Add
      </button>
    </form>
    <div
      v-for="todo in todos" 
      key="todo.id"
      class="card mt-2"
    >
      <div class="card-body">
        {{ todo.subject }}
      </div>
    </div>
  </div>
</template>
<script>
import { ref } from 'vue'

export default {
  setup() {
    const todo = ref('')
    const todos = ref([
    ])

    const onsubmit = ( ) => {
      todos.value.push({
        id:Date.now(),
        subject:todo.value
      })
    }

    return{
      todo,
      todos,
      onsubmit
    }
  }
}
</script>

<style scoped>

</style>
