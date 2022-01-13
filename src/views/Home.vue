<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <TodoApp msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import TodoApp from '@/components/TodoApp.vue'

export default {
  name: 'Home',
  components: {
    TodoApp
  }
}
</script>
