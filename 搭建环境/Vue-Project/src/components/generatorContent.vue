<template>
  <div id = 'array'>
    Set结构
  </div>   
</template>

<script>
export default {
  name: 'setContent',
  methods: {
    demo () {
      console.log('公司Generator函数')
      //  next方法可以带一个参数，该参数会被当做上一条yield语句的返回值
      let a = this.foo(5)
      console.log(a.next())
      console.log(a.next(6))
    },
    * foo (x) {
      let y = 2 * (yield (x + 1))
      let z = yield (y / 3)
      return (x + y + z)
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
