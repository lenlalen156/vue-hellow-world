<template>
  <div id="app">
    <Header />
    <Todos />
  </div>
</template>

<script>
import Header from './components/Header'
import Todos from './components/Todos'

export default {
  name: 'App',
  components:{Header,Todos}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
