<template>
  <div id = 'array'>
    数组的扩展
    <p>Nodelist1</p>
    <p>Nodelist2</p>
    <p>Nodelist3</p>
    <p>Nodelist4</p>
    <p>Nodelist5</p>
  </div>   
</template>

<script>
export default {
  name: 'HelloWorld',
  methods: {
    demo () {
      let arrayLike = {
        '0': 'a',
        '1': 'b',
        '2': 'c',
        length: 3
      }
      //  ES5的写法
      var arr1 = [].slice.call(arrayLike)
      console.log(arr1)
      //  ES6的写法
      let arr2 = Array.from(arrayLike)
      console.log(arr2)
      //  NodeList对象
      let ps = document.querySelectorAll('p')
      Array.from(ps).forEach(function (p) {
        console.log(p)
      })
      //  arguments对象
      let args = Array.from(arguments)
      console.log(args)
      //  Array.from()可以将各种值转为真正的数组，并且提供map功能。只要有一个原始的数据结构，就可以先对它的值进行处理，然后转为规范的数组解构，进而可以使用数量众多的数组方法。
      let meSay = Array.from({ length: 2 }, () => '我勇牛逼')
      console.log(meSay)
      //  Array.from()将字符串转为数组，然后返回字符串的长度
      console.log(this.countSymbols('woyong'))
      this.arrayOf()
    },
    arrayOf () {
      //  Array.of方法用于将一组值转换为数组
      console.log('Array.of')
      console.log(Array.of(3))
      console.log(Array.of(3, 11, 8))
      //  Array方法没有参数、有一个参数或有三个参数，返回结果都不一样。只有参数个数不少于2个时，Array()才会返回由参数组成的新数组。参数个数只有一个时，实际上是指定数组的长度
      console.log(Array())
      console.log(Array(3))
      console.log(Array(1,2))
    },
    countSymbols (string) {
      return Array.from(string).length
    }
  },
  created () {
    this.demo(1, 2, 3)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
