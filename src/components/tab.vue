<template>
    <div class="helper">
        <span class="left">{{unFinshedCompleted}} item left</span>
        <span class="tabs">
            <span v-for="state in states" :key="state" :class="[state, select === state ? 'actived' : '']" @click="tabChange(state)">{{state}}</span>
        </span>
        <span class="clear" @click="clearAllCompleted">Clear completed</span>
    </div>
</template>
<script>
    export default {
        data () {
            return {
                states: ['all', 'active', 'completed'],
            }
        },
        props: {
            select: {
                type: String,
                default: 'all'
            },
            todos: {
                type: Array,
                default: []
            }
        },
        computed: {
            unFinshedCompleted() {
                return this.todos.filter(todo => todo.completed === false).length
            }
        },
        methods: {
            tabChange(state) {
                this.$emit('change', state)
            },
            clearAllCompleted() {
                this.$emit('clear')
            }
        }
    }
</script>
<style lang="stylus" scoped>
    .helper
        font-weight: 100
        display: flex
        justify-content: space-between
        padding: 5px 0
        line-height: 30px
        background-color: #fff
        font-size: 14px
        font-smoothing: antialiased
        .left, .clear, .tabs
            padding: 0 10px
            box-sizing: border-box
        .left, .clear
            width: 150px
        .left
            text-align: left
        .clear
            text-align: right
            cursor: pointer
        .tabs
            width: 200px
            display: flex
            justify-content: space-around
            * 
                display: inline-block
                padding: 0 10px
                cursor: pointer
                border: 1px solid rgba(175,47,47,0)
                &.actived
                    border-color: rgba(175,47,47,0.4)
                    border-radius: 5px
</style>

