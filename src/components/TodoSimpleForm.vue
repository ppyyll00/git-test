<template>
  <form @submit.prevent="onsubmit" >
    <div class="d-flex">
      <div class="flex-grow-1 mr-2">
        <input
          placeholder="to do list"
          v-model="todo"
          class="form-control"
          type="text"
        >
      </div>
      <div>
        <button
        type="submit"
        class="btn btn-primary"
        >
          Add
        </button>
      </div>      
    </div>
    <div v-show="hasErrer" style="color: red">
      This field cannot be empty
    </div>
    </form>
    
</template>

<script>
import { ref } from 'vue'

export default {
  setup(props, context) { /*왜인지 모르겠지만 props를 넣어야 연결됨*/
    const todo = ref('')
    const hasErrer = ref(false)

    const onsubmit = () => {
      if (todo.value === '') {
        hasErrer.value = true
      } else {
        context.emit('add-todo', { /*add-todo가 시작되면 데이터를 부모한테 보내준다.*/
          id:Date.now(),
          subject:todo.value,
          completed: false,
        });
        hasErrer.value = false;
        todo.value = ''
      }      
    }

    return {
      todo,
      hasErrer,
      onsubmit,
    }
  }
}
</script>

<style>
</style>
