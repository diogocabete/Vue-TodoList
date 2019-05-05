<template>
  <div id="app">
    <Header />
    <AddTodo v-bind:todos="todos"/>
    <TodoList v-bind:todos="todos" v-on:deleteTodo="deleteTodo"/>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import Header from './components/Header.vue'
import AddTodo from './components/AddTodo.vue'

export default {
  name: 'app',
  components: {
    TodoList,
    Header,
    AddTodo
  },
  data(){
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(index) {
      //this.todos = this.todos.filter(todo => todo.title != index)
      this.todos.splice(index, 1);
    }
  },
  watch: {     //watch watches the todosarray for changes, when a change
    todos: {   //occures then it sets an item 'todos' in local storage
      handler: function() {
        localStorage.setItem('todos', JSON.stringify(this.todos));
      },
      //deep: true lets it search nested values
      deep: true
    }
  },
  mounted() {
    //when the app is mounted, look in localstorage for a todos item
    //if it exists set the todos array to it
    if (localStorage.getItem('todos')) {
      try{
        this.todos = JSON.parse(localStorage.getItem('todos'));
      } catch(e) {
        localStorage.removeItem('todos');
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 40px;
}
</style>
