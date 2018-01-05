<template>
  <div id = 'Promise'>
    Promise对象
  </div>   
</template>

<script>
export default {
  name: 'setContent',
  methods: {
    demo () {
      console.log('异步操作和async函数')
    }
  },
  created () {
    this.demo()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
