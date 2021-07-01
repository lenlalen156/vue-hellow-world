<template>
  <TodoItem v-bind:key="todo.id" v-for="todo in todos" v-bind:todoProps="todo"/>
</template>

<script>
import {ref} from 'vue'
import TodoItem from './TodoItem'

export default {
  name:'Todos',
  components:{TodoItem},
  setup(){
    const todos = ref([
      {
        id: 1,
        title: 'viec 1',
        completed: false
      },{
        id: 2,
        title: 'viec 2',
        completed: false
      },{
        id:3 ,
        title: 'viec 3',
        completed: false
      },
    ])

    return {
      todos
    }
  }
}
</script>

<style>

</style>