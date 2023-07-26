<template>
  <div class="container">
    <h2>To-Do List</h2>
    <TodoSimpleForm @add-todo="addTodo" />

    <div v-if="!todos.length">
      추가된 Todo가 없습니다
    </div>
    <TodosForm :todos="todos" @toggle-todo="toggleTodo"/> <!--props를 이용하여 부모에 있는 "todos"를 todos 이름으로 자식컴포넌트(TodosForm) 에 전달-->
    <!-- 자식한테 'toggle-todo'로 받은 index를 toggleTodo라는 함수에 적용시킨다. -->
    
  </div>
</template>
<script>
import { ref } from 'vue'
import TodoSimpleForm from '@/components/TodoSimpleForm.vue'
import TodosForm from '@/components/TodosForm.vue'

export default {
  components: {
    TodoSimpleForm,
    TodosForm
  },
  setup() {
    const todos = ref([]) /*[] = array = 배열*/

    const addTodo = (todo) => {
      todos.value.push(todo);
    }

    const deleteTodo = (index) => {
      todos.value.splice(index,1)
    }

    const toggleTodo = (index) => {
      todos.value[index].completed = !todos.value[index].completed  /* todos를 TodosForm으로 받아서 브이포로 사용하고 그 인덱스를 다시 부모한테 전달했음 */ 
      /* 인풋의 인덱스가 트루면 펄스로, 펄스면 트루로 변경, (마우스 클릭시 적용) */
    }

    return{
      todos,
      addTodo,
      deleteTodo,
      toggleTodo,
    }
  }
}
</script>

<style scoped>

</style>
