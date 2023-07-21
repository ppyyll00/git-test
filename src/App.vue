<template>
  <div>
    <h2>To-Do List</h2>
    <TodoSimpleForm @add-todo="addTodo" />

    <div v-if="!todos.length">
      추가된 ToDo List가 없습니다.
    </div>
    <div
      v-for="(todo,index) in todos" 
      key="todo.id"
      class="card mt-2"
    >
      <div class="card-body d-flex align-items-center">
        <div clsss="form-check flex-grow-1">
          <input 
            class="form-check-input" 
            type="checkbox"
            v-model="todos.completed"
          >
          <label class="form-check-label">
            {{ todo.subject }}
          </label>
        </div>
        <div>
          <button 
            class="btn btn-danger btn-sm"
            @click="deleteTodo(index)"
          >
            delete
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { ref } from 'vue'
import TodoSimpleForm from '@/components/TodoSimpleForm.vue'

export default {
  components: {
    TodoSimpleForm
  },
  setup( ) {
    const todo = ref('')
    const todos = ref([ ])

    const addTodo = (todo) => {
      todos.value.push(todo);
    }

    const deleteTodo = (index) => {
      todos.value.splice(index,1)
    }

    return{
      todo,
      todos,
      addTodo,
      deleteTodo,
    }
  }
}
</script>

<style scoped>

</style>
