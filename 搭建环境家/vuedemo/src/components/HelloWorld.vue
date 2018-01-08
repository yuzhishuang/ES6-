  <template>
    <div class="hello">
      <h1>{{ msg }}</h1>
      <objectPart />
      <setContent />
      <iteratorContent />
      <generatorContent />
      <asyncContent />
      <finalContent />
    </div>
  </template>

  <script>
  import objectPart from './Object.vue'
  import setContent from './setContent.vue'
  import iteratorContent from './iteratorContent.vue'
  import generatorContent from './generatorContent.vue'
  import asyncContent from './asyncContent.vue'
  import finalContent from './finalContent.vue'
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
        //  扩展运算符（spread）是三个点（...）。它好比rest参数的逆运算，将一个数组转为用逗号分隔的参数序列
        console.log('扩展运算符')
        console.log(...[1, 2, 3])
        //  替代数组的apply方法，由于扩展运算符可以展开数组，所以不再需要apply方法将数组转为函数的参数了
        //  ES5写法
        let arr1 = [0, 1, 2]
        this.f.apply(null, arr1)
        //  ES6写法
        let arr2 = [12, 23, 34]
        this.f(...arr2)
        //  下面是扩展运算符取代apply方法的一个实际的例子，应用Math.max方法简化求数组最大元素的写法
        //  ES5的写法
        let arr3 = [14, 3, 77]
        console.log(Math.max.apply(null, [14, 3, 77]))
        //  ES6的写法
        console.log(Math.max(...arr3))
        //  另一个例子是通过push函数将一个数组添加到另一个数组的尾部
        //  ES5的写法
        let arr4 = Array.prototype.push.apply([1, 2, 5], [9, 8])
        console.log(arr4)
        let arr5 = arr1.push(...arr2)
        console.log(arr5)
        //  扩展运算符的应用，合并数组
        //  es5
        let arr6 = ['a', 'b', 'c']
        let arr7 = ['d']
        var arr8 = ['e', 'f']
        console.log(arr6.concat(arr7, arr8))
        //  es6
        console.log([...arr6, ...arr7, ...arr8])
        //  Map结构
        let map = new Map([
          [1, 'one'],
          [2, 'two'],
          [3, 'three']
        ])
        console.log(map)
        this.jiantouFunction()
      },
      jiantouFunction () {
        //  es6允许使用箭头(=>)定义函数
      },
      f (x, y, z) {
        console.log(x, y, z)
      }
    },
    created () {
      this.ArrayDemo()
    },
    components: {
      objectPart: objectPart,
      setContent: setContent,
      iteratorContent: iteratorContent,
      generatorContent: generatorContent,
      asyncContent: asyncContent,
      finalContent: finalContent
    }
  }
  </script>

  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  </style>
