<template>
  <div id="app">
    <div class="todo-container">
      <AddTodo v-on:add-todo="addTodo" />
      <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    </div>
  </div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';


export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return{
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {      //json placeholder mimics a real backend however the data that is posted to it doesn't persist
        title: title,
        completed: completed
      })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));    
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=7')   //this uses 'json placeholder' as a fake rest API and returns a promise which is handled with a the 'then' and 'catch' functions
      .then(res => this.todos = res.data)                             
      .catch(err => console.log(err));
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
body{
  font-family: 'Bai Jamjuree', sans-serif;
  font-size: 16px;
  line-height: 1.4;
}
.btn{
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
  border-radius: 5px;
}
.btn:hover{
  background: #666;
}
#app{
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  width: 100%;
}
.todo-container{
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  width: 40%;
  height: auto;
}
</style>
