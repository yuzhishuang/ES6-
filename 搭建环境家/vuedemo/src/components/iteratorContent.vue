  <template>
    <div class="hello">
    </div>
  </template>

  <script>
  export default {
    methods: {
      iteratorDemo () {
        console.log('iterator和for...of循环')
        //  为对象添加Iterator接口的例子
        let obj = {
          data: ['hello', 'world'],
          [Symbol.iterator]() {
            const self = this
            let index = 0
            return {
              next () {
                if (index < self.data.length) {
                  return {
                    value: self.data[index++],
                    done: false
                  }
                } else {
                  return { value: undefined, done: true}
                }
              }
            }
          }
        }
        for (let [k, v] of obj) {
          console.log(k, v)
        }
        //  对于类似数组的对象（存在数值键名和length属性），部署Iterator接口有一个简便方法，就是Symbol.iterator方法直接引用数组的Iterator接口
        let iterable = {
          0: 'a',
          1: 'b',
          2: 'c',
          length: 3,
          [Symbol.iterator]: Array.prototype[Symbol.iterator]
        }
        for (let item of iterable) {
          console.log(item)
        }
        //  可以覆盖原生的Symbol.iterator方法达到修改遍历器行为的目的
        let str = new String("hi")
        console.log([...str])
        str[Symbol.iterator] = function () {
          return {
            next: function () {
              if (this._first) {
                this._first = false
                return { value: 'bye', done: false}
              } else {
                return { done: true}
              }
            },
            _first: true
          }
        }
        console.log([...str])
        //  JavaScript原有的for...in循环，只能获得对象的键名，不能直接获取键值。ES6提供for...of循环，允许遍历获得键值
        let arr1 = ['a', 'b', 'c', 'd']
        for (let a in arr1) {
          console.log(a)
        }
        for (let a of arr1) {
          console.log(a)
        }
        //  Set和Map结构也原生具有Iterator接口，可以直接使用for...of循环
        let engines = new Set(['Gecoko', 'Trident', 'Webkit', 'Webkit'])
        for (let a of engines) {
          console.log(a)
        }
        let es6 = new Map()
        es6.set('edition', 6)
        es6.set('committee', 'TC39')
        es6.set('name', 'yzs')
        for (let [k, v] of es6) {
          console.log(k + ':' + v)
        }
      }
    },
    created () {
      this.iteratorDemo()
    }
  }
  </script>

  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  </style>
