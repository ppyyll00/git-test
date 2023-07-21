<template>
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
    <div v-if="hasErrer">Errer</div>
</template>

<script>
import { ref } from 'vue'
export default {
  setup(props, context) {
    const todo = ref('')
    const hasErrer = ref(false)

    const onsubmit = ( ) => {
      if (todo.value === '') {
        hasErrer.value = true
      } else {
        context.emit('add-todo' , { /*add-todo가 시작되면 데이터를 부모한테 보내준다.*/
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
