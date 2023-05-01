<template>
  <TodoSimpleForm @add-todo="addTodo"/>
</template>

<script>
  // ref : 로 데이터를 바인딩함
  import TodoSimpleForm from './components/TodoSimpleForm.vue';
  // import {reactive} from 'vue';
  export default {
    components: {
      TodoSimpleForm, 
    },
    // 화면에 데이터나 이벤트를 그려지게함
    setup() {
      const addTodo = (todo) => {
        console.log(todo)
      }
      return {
        TodoSimpleForm, 
        addTodo
      };
    }
  }
</script>
<style>
  .todo {
    color: gray;
    text-decoration: line-through;
  }
</style>