<template>
  <p :class="['todo-item', todoProps.completed ? 'is-completed' : '']" >
    <input type="checkbox" :checked="todoProps.completed" />
    {{todoProps.title}}
    <button class="del-btn">Delete</button>
    </p>
</template>

<script>


export default {
  name: 'TodoItem',
  props:['todoProps'],
}
</script>

<style>
  .todo-item{
    background: #f4f4f4;
    padding: 10px;
    margin: 0;
    border-bottom: solid 1px gray;
  }
  .is-completed{
    text-decoration: line-through;
  }
  .del-btn{
    background: #ff0000;
    color: #fff;
    border: none;
    cursor:pointer;
    float: right;
  }
</style>