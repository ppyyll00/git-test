<template>
  <div 
      v-for="(todo, index) in todos"
      :key="todo.id"
      class="card mt-2"
    >
      <div class="card-body p-2 d-flex align-items-center">
        <div class="form-check flex-grow-1">
          <input 
            class="form-check-input" 
            type="checkbox"
            :value="todo.completed"
            @change="toggleTodo(index)"            
          ><!-- @change = 인풋값이 변경될때마다 toggleTodo라는 함수를 실행시킴, index는 todos fmf 브이포 로 돌릴떄 나오는 index다 -->
          <label 
            class="form-check-label"
            :class="{ todo: todo.completed }"
          >
            {{ todo.subject }}
          </label>
        </div>
        <div>
          <button 
            class="btn btn-danger btn-sm"
            @click="deleteTodo(index)"
          >
            Delete
          </button>
        </div>
      </div>
    </div>
</template>
<script>
export default {
  // props: ['todos'] /*부모컴포넌트에 todos를 받기 위해 삽입*/
  props: {
    todos: {
      type: Array, /*App에서 todos를 array로 정의했기 때문에 배열로 받아야 한다.*/
      required: true, /*todos를 배열로 해줄거기 때문에 true로 설정 */
    }
  },
  setup(props, context) {
    const toggleTodo = (index) => {
      context.emit('toggle-todo', index) /*인풋값이 변경될때 input값을 'toggle-todo'이름으로 부모한테 넘기겠다. */
    }

    return {
      toggleTodo,
    }
  }
}
</script>
<style></style>
