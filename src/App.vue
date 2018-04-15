<template>
  <div id="app">
    <m-header></m-header>
    <todo-list></todo-list>
    <m-footer></m-footer>
  </div>
</template>

<script>
  import MHeader from 'components/m-header'
  import MFooter from 'components/m-footer'
  import TodoList from 'components/todolist'
  export default {
    components: {
      MHeader,
      MFooter,
      TodoList
    }
  }
</script>

<style lang="stylus" scoped>
  #app
    position: absolute
    left: 0
    right: 0
    top: 0
    bottom: 0
    #cover
      position: absolute
      left: 0
      top: 0
      right: 0
      bottom: 0
      background-color: #999
      opacity: .9
      z-index: -1
</style>

