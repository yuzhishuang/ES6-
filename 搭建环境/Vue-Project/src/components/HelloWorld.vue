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
    demo () {
      //  Number.isFinite()用来检查一个数值是否非无穷尽
      console.log(Number.isFinite(15))
      console.log(Number.isFinite(NaN))
      //  Number.isNaN()用来检查一个值是否为NaN
      console.log(Number.isNaN(NaN))
      console.log(Number.isNaN(15))
      //  这两个新方法于传统的全局方法isFinite()和isNaN()的区别在于，传统方法先调用Number()将非数值转为数值，再进行判断，而新方法只对数值有效，对于非数值一律返回false
      console.log(isNaN(NaN))
      console.log(isNaN('NaN'))
      console.log(Number.isNaN('NaN'))
      //  Number.isInteger()用来判断一个值是否为整数。需要注意的是，在JavaScript内部，整数和浮点数是同样的储存方法，所以3和3.0被视为同一个值
      console.log('判断是否为整数')
      console.log(Number.isInteger(25))
      console.log(Number.isInteger(25.0))
      console.log(Number.isInteger(25.3))
      //  ES6在Number对象上新增了一个极小的常量-Number.EPSILON
      console.log('Number.EPSILON')
      console.log(Number.EPSILON)
      let a = this.withinErrorMargin(0.1 + 0.2, 0.3)
      let b = this.withinErrorMargin(0.1 + 0.3, 0.3)
      console.log('a=' + a)
      console.log('b=' + b)
      //  Math.trunc方法用于去除一个数的小数部分，返回整数部分
      console.log('Math.trunc')
      console.log(Math.trunc(4.1))
      //  对于非数值，Math.trunc内部使用Number方法将其先转化为数值
      console.log(Math.trunc('123.654'))
    },
    withinErrorMargin (left, right) {
      return Math.abs(left - right) < Number.EPSILON
    }
  },
  created () {
    this.demo()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
