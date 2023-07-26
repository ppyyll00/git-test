<template>
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
</template>
<script>
export default defineComponent({
  setup() {
    
  },
})
</script>
<style></style>
