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
  setup() {
    const todo = ref('')
    const hasErrer = ref(false)

    const onsubmit = ( ) => {
      if (todo.value === '') {
        hasErrer.value = true
      } else {
        todos.value.push({
        id:Date.now(),
        subject:todo.value,
        completed: false, /*완료가 되어있는지 안되어있는지, 첨엔 완료안되어있기 때문에 false로 설정*/
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
