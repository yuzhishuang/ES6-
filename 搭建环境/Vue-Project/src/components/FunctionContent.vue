<template>
  <div id = 'fun'>
  </div>   
</template>

<script>
export default {
  name: 'HelloWorld',
  methods: {
    demo () {
      console.log('function')
      //  在ES6之前，不能直接为函数的参数指定默认值，只能采用变通的方法
      //  缺点：如果参数y赋值了，但是对应的布尔值为false，则该赋值不起作用。就像第三条一样，参数y等于空字符，结果被改为默认值，还有两种写法
      this.log('Hello')
      this.log('Hello', 'China')
      this.log('Hello', '')
      //  ES6允许为函数的参数设置默认值，即直接写在参数定义的后面
      console.log('ES6写法')
      this.Es6Log('hello')
      this.Es6Log('hello', 'world')
      this.Es6Log('hello', '')
      //  与解构赋值默认值结合使用
      console.log('与解构赋值默认值结合使用')
      console.log(this.foo({}))
      console.log(this.foo({x: 1}))
      console.log(this.foo({x: 1, y: 2}))
      //  console.log(this.foo())
      //  利用参数默认值，可以指定某一个参数不得省略，如果省略就抛出一个错误
      this.foo1()
      //  ES6引入了rest参数（形式为“···变量名”）,用于获取函数的多余参数，这样就不需要arguments对象了。rest参数搭配的变量是一个数组，该变量将多余的参数放入其中。
      console.log(this.add(1, 2, 3))
      //  rest参数改写数组push方法的例子
      let arr1 = []
      this.push(arr1, 1, 2, 3, 4)
    },
    push (array, ...items) {
      items.forEach((item) => {
        array.push(items)
        console.log(items)
      })
      //  嵌套的箭头函数
      console.log('嵌套的箭头函数')
      //  Reflect.ownKeys方法可以返回所有类型的键名，包括常规键名和Symbol键名
      let obj = {
        [Symbol('my_key')]: 1,
        enum: 2,
        nonEnum: 3
      }
      console.log(Reflect.ownKeys(obj))
      //  Proxy概述
      this.proxyYzs()
    },
    proxyYzs () {
      //  一个技巧是将Proxy对象设置到object.proxy属性，从而可以在object对象上使用
      let proxy = new Proxy({}, {
        get: function (target, property) {
          return 35
        }
      })
      let obj1 = Object.create(proxy)
      console.log(obj1.time)
      console.log('Proxy实例的方法')
      let person = {name: '张三'}
      let proxy1 = new Proxy(person, { get: function (target, property) { if (property in target) { return target[property] } else { throw new ReferenceError(property + 'does not exist.') } } })
      console.log(proxy1.name)
      //  console.log(proxy1.age)   报错
      //  get方法可以继承
      let proto = new Proxy({}, {
        get (target, propertyKey, receiver) {
          console.log('GET' + propertyKey)
          return target[propertyKey]
        }
      })
      let obj2 = Object.create(proto)
      console.log(obj2.xxx)
      this.proxySet()
    },
    proxySet () {
      console.log('set()方法')
    },
    add (...values) {
      let sum = 0
      for (let val of values) {
        sum += val
      }
      return sum
    },
    throwIfMissing () {
      console.log('Missing parameter')
    },
    foo1 (mustBeProvided = this.throwIfMissing()) {
      return mustBeProvided
    },
    foo ({x, y = 5}) {
      console.log(x, y)
    },
    log (x, y) {
      //  y = y || 'world'
      //  写法一
      //  if (typeof y === 'undefined') {
        //  y = 'World'
      //  }
      //  写法二
      if (arguments.length === 1) {
        y = 'World'
      }
      console.log(x, y)
    },
    Es6Log (x, y = 'World') {
      console.log(x, y)
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
