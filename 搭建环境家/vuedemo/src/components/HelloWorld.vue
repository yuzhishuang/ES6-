<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
      <br>
      <li><a href="http://vuejs-templates.github.io/webpack/" target="_blank">Docs for This Template</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    ArrayDemo () {
      //  数组实例的copyWithin方法，在当前数组内部将制定位置的成员复制到其他位置（会覆盖原有成员），然后返回当前数组。也就是说，使用这个方法会修改当前数组。
      let array1 = [1,2,3,4,5]
      console.log(array1.copyWithin(0, 3))
      console.log(array1.copyWithin(0, 3, 4))
      //  数组实例的find方法，用于找出第一个符合条件的数组成员。它的参数是一个回调函数，所有数组成员依次执行该回调函数，直到找出第一个返回值为true的成员，然后返回该成员金，如果没有符合条件的成员，则返回undefined
      console.log(array1.find((n) => n < 5))
      //  find方法的回调函数可以接受3个参数，依次为当前的值、当前的位置和原数组
      let locationArray = array1.find(function(value, index, arr) {
        return value > 4
      })
      console.log(locationArray)
      //  findIndex方法中，返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回-1
    }
  },
  created () {
    this.ArrayDemo()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
