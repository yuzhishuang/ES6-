  <template>
    <div class="hello">
    </div>
  </template>

  <script>
  export default {
    methods: {
      generatorDemo () {
        console.log('Generator函数')
        //  Generator函数是ES6提供的一种异步编程解决方案
        let hw = this.helloworldGenerator()
        console.log(hw.next())
        console.log(hw.next())
        console.log(hw.next())
        let arr = [1, [[2, 3], 4], [5, 6]]
        let float = function* (a) {
          let length = a.length
          for(let i = 0; i < length; i++) {
            let item = a[i]
            if (typeof item !== 'number') {
              yield* float(item) 
            } else {
              yield item
            }
          }
        }
        console.log(float)
        for (var f of float(arr)) {
          console.log(f)
        }
        //  next方法可以带一个参数，该参数会被当做上一条yield语句的返回值
        //  for...of循环可以自动遍历Generator函数，且此时不再需要调用next方法
        for (let v of this.foo()) {
          console.log(v)
        }
        //  对象jane原生不具备Iterator接口，无法用for...of遍历。我们通过Generator函数objectEntries为它加上遍历器接口，就可以用for...of遍历了，加上遍历器接口的另一种写法是，将Generator函数加到对象的symbol.iterator属性上
        //  let jane = { first: 'Jane', last: 'Doe'}
        //  jane[Symbol.iterator] = this.objectEntries
        //  for (let [key, value] of jane) {
          //  console.log(`${key}: ${value}`)
        //  }
      },
      * objectEntries () {
        let propKeys = Object.keys(this)
        for (let propKey of propKeys) {
          yield [propKey, this[propKey]]
        }
      },
      * foo () {
        yield 1;
        yield 2;
        yield 3;
        yield 4;
        yield 5;
        return 6;
      },
      * helloworldGenerator () {
        yield 'hello'
        yield 'world'
        return 'ending'
      },
      * f (x) {
        for (let i = 0; true; i++) {
          let reset = yield i
          if (reset) { i = -1}
        }
      }
    },
    created () {
      this.generatorDemo()
    }
  }
  </script>

  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  </style>
