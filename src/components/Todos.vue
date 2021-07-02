<template>
  <AddTodo  @add-todo="addTodo" />
  <TodoItem :key="todo.id" 
  v-for="todo in todos" 
  :todoProps="todo" 
  @item-completed="markCompleted"
  @delete-item="deleteTodo"
  />
</template>

<script>
import {ref} from 'vue'
import TodoItem from './TodoItem'
import AddTodo from './AddTodo.vue'
// import { v4 as uuidv4 } from 'uuid'
import axios from 'axios'

export default {
  name:'Todos',
  components:{TodoItem, AddTodo},
  setup(){
    const todos = ref([])

    const getAllTodo = async () => {
      try{
        const res = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
        // console.log(res.data)
        todos.value = res.data
      }catch (error){
        console.log(error)
      }
    }
    getAllTodo()

    const markCompleted = async id => {
      todos.value = todos.value.map(todo => {
        if(todo.id === id) todo.completed = !todo.completed;
        return todo
      })
    }

    const deleteTodo = id => {
      try{
         axios.delete(`http://jsonplaceholder.typicode.com/todos/${id}`)
        todos.value = todos.value.filter(todo => todo.id !== id)
      }catch(error){
        console.log(error)
      }

      // todos.value = todos.value.filter(todo => todo.id !== id)
    }

    const addTodo = async newTodo => {
      try{
        const res = await axios.post('http://jsonplaceholder.typicode.com/todos/',newTodo)
        todos.value.push(res.data)
      }catch(error){
        console.log(error)
      }

      // console.log(newTodo.id)
      // todos.value.push(newTodo)
    }

    return {
      todos,
      markCompleted,
      deleteTodo,
      addTodo,
      getAllTodo
    }
  }
}
</script>

<style>

</style>