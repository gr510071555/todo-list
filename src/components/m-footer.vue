<template>
  <div id="footer">
      <span>Written By {{this.author}}</span>
  </div>
</template>
<script>
    export default {
        data () {
            return {
                author: 'gr'
            }
        }
    }
</script>
<style lang="stylus" scoped>
    #footer
        margin-top 40px
        text-align center
        color: #bfbfbf
        font-size: 10px
        text-shadow: 0 1px 0 rgba(255, 255, 255, 0.5)
</style>
