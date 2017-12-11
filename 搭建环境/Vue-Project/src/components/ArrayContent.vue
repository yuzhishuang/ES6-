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
<<<<<<< HEAD
      console.log(Array())
      console.log(Array(3))
      console.log(Array(1,2))
      //  扩展运算符是三个点...。它好比rest参数的逆运算，将一个数组转为用逗号分隔的参数序列
      console.log('扩展运算符')
      console.log(...[1, 2, 3])
=======
      //  console.log(Array(1))
      //  console.log(Array(3))
      //  console.log(Array(1, 2))
      //  fill方法使用给定值填充数组
      let arr2 = ['a', 'b', 'c']
      console.log(arr2.fill(7))
      let arr3 = new Array(3).fill(7)
      console.log(arr3)
      //  fill方法用于空数组的初始化非常方便。数组中已有的元素，会被全部抹去。fill方法还可以接受第二个和第三个参数，用于指定填充的起始位置和结束位置
      console.log(arr2.fill(8, 1, 2))
      //  数组实例的entries()、keys()、values(),keys()是对键名的遍历，values()是对键值的遍历，entries()是对键值对的遍历
      console.log('entries')
      for (let index of ['a', 'b'].keys()) {
        console.log(index)
      }
      //  for (let elem of ['a', 'b'].values()) {
        //  console.log(elem)
      //  }
      for (let [index, value] of ['a', 'b'].entries()) {
        console.log(index, value)
      }
      //  如果不适用for----of循环，可以手动调用遍历器对象的next方法进行遍历
      let arr4 = ['a', 'b', 'c']
      let entries = arr4.entries()
      console.log(entries.next().value)
      console.log(entries.next().value)
      console.log(entries.next().value)
      this.includes()
    },
    includes () {
      //  返回一个布尔值，表示某个数组是否包含给定的值，该方法的第二个参数表示搜索的起始位置
      //  NaN非数值
      console.log('includes')
      let arr1 = [1, 2, 3]
      console.log(arr1.includes(2))
      console.log(arr1.includes(4))
      console.log(arr1.includes(2, 3))
      console.log([1, 2, NaN].includes(NaN))
      let arr2 = Array(3)
      console.log(arr2)
      //  数组推导中，for···of结构总是写在最前面，返回的表达式写在最后面
      //  ES7中语法
      //  let arr3 = [1990, 1991, 1992, 1994, 2000, 2001, 2005]
      //  let arr4 = [for (year of arr3) if (year > 2000) year]
      //  console.log(arr4)
>>>>>>> 4d8333a8f4457fdc8975c50426246c2245228c54
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
