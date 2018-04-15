<template>
  <div class="real-app">
    <input 
        type="text"
        class="add-input"
        autofocus="autofocus"
        :placeholder="placeholder"
        @keyup.enter="addTodo"
        ref="todoList"
    >
    <list :todo="todo" v-for="todo in filterTodos" :key="todo.id" @delete="deleteTodo" />
    <tab :select="select" :todos="todos" @change="tabChange" @clear="clearAllCompleted"></tab>
  </div>
</template>
<script>
    import Tab from 'components/tab'
    import List from 'components/list'
    export default{
        data () {
            return {
                id: 0,
                placeholder: '接下来实现什么目标?',
                todos: [],
                select: 'all'              
            }
        },
        computed: {
          filterTodos() {
              if (this.select === 'all') {
                  return this.todos
              }
              const completed = this.select === 'completed'
              return this.todos.filter(todo => todo.completed === completed)
          }  
        },
        methods: {
          addTodo() {
              this.todos.unshift({
                  id: this.id++,
                  content: this.$refs.todoList.value.trim(),
                  completed: false
              })
              this.$refs.todoList.value = ''
          },
          deleteTodo(id) {
              this.todos.splice(this.todos.findIndex(todo => todo.id === id), 1)
          },
          tabChange(state) {
              this.select = state
          },
          clearAllCompleted() {
              this.todos = this.todos.filter(todo => todo.completed === false)
          }  
        },
        components: {
            Tab,
            List
        }
    }
</script>
<style lang="stylus" scoped>
    .real-app
        width: 600px
        margin: 0 auto
        box-shadow: 0 0 5px #666
        .add-input
            position: relative
            margin: 0
            width: 100%
            font-size: 24px
            font-family: inherit
            font-weight: inherit
            line-height: 1.4em
            border: 0
            outline: none
            color: inherit
            padding: 6px
            border: 1px solid #999
            box-shadow: inset 0 -1px 5px 0 rgba(0, 0, 0, 0.2)
            box-sizing: border-box
            font-smoothing: antialiased
            padding: 16px 16px 16px 60px
            border: none
            box-shadow: inset 0 -2px 1px rgba(0,0,0,0.03)
</style>
