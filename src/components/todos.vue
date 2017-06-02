<template>
  <div id="fuck" class="container-fluid">
    <nabar :heading="heading"></nabar>
    <addTodo :todos="todos"></addTodo>
    <todoItem :todos="todos" :hasFinish="hasFinish"></todoItem>
  </div>
</template>

<style media="screen">

</style>
<script>
import nabar from './nabar'
import todoItem from './todoItem'
import addTodo from './addTodo'
export default {
  name: 'fuck',
  data () {
    return {
      todos: [],
      hasFinish: []
    }
  },
  components: {
    nabar,
    todoItem,
    addTodo
  },
  computed: {
    heading :function(todo){
      return this.todos.filter(function(todo){
        return !todo.flag;
      }).length;
    }
  }
}
</script>
