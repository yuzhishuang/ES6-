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
      console.log('公司Set结构')
      //  Set结构的实例默认可遍历，其默认遍历器生成函数就是它的values方法，这意味着，可以省略values方法，直接用for...of循环遍历Set
      let set = new Set(['red', 'green', 'blue', 'red'])
      for (let i of set) {
        console.log(i)
      }
      //  更便捷的数组去重
      let arr = [1, 2, 3, 4, 5, 4, 3, 2, 1]
      console.log([...new Set(arr)])
      //  数组的map和filter方法也可以用于Set了
      let arr1 = new Set([1, 2, 3])
      let arr2 = new Set([...arr1].map(x => x * 2))
      console.log(...arr2)
      //  Set结构的实例的forEach方法用于对每个成员执行某种操作，没有返回值
      let set1 = new Set([1, 2, 3])
      set1.forEach((value, key) => console.log(value * 2))
      //  ES6提供了Map数据结构。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键
      console.log('Map')
      this.mapContent()
    },
    mapContent () {
      let m = new Map()
      let o = {p: 'Hello World'}
      m.set(o, 'content')
      console.log(m.get(o))
      //  Map也可以接受一个数组作为参数。该数组的成员是一个个表示键值对的数组
      let map = new Map([['name', '张三'], ['title', 'Author']])
      console.log(map.size)
      console.log(map.has('name'))
      console.log(map.get('name'))
      console.log(['a'] === ['a'])
      //  size属性
      console.log('size属性')
      let map1 = new Map([['name', 'yzs'], ['age', 18]])
      console.log(...map1.set('height', 186))
      //  数组的map方法，filter方法，可以实现Map的遍历和过滤（Map本身没有map方法和filter方法）
      let map2 = new Map([[1, 'a'], [2, 'b'], [3, 'c']])
      let map3 = new Map([...map2].filter(([k, v]) => k < 3))
      console.log('filter')
      console.log(...map3)
      let map4 = new Map([...map2].map(([k, v]) => [k * 2, '_' + v]))
      console.log(...map4)
      //  Map转为对象
      //  如果Map的所有键都是字符串，则其可以转为对象
      let myMap = new Map().set('yzs', true).set('no', false)
      let myMap1 = this.strMapToObj(myMap)
      console.log(myMap1)
      let myMap2 = this.objToStrMap({'age': 18, 'yzs': true})
      console.log(...myMap2)
      //  Map转为JSON要区分两种情况。一种情况是，Map的键名都是字符串，这时可以选择转为对象json
      let myMap3 = new Map().set('yzs', true).set('no', false)
      console.log(this.strMapToJson(myMap3))
      //  另一种情况是，Map的键名有非字符串，这时可以选择转为数组JSON
      let myMap4 = new Map().set(true, 7).set({foo: 3}, ['abc'])
      console.log(this.mapToArrayJson(myMap4))
      //  JSON转为Map，正常情况下所有键名都是字符串
      let myMap5 = '{"yzs": true, "age": 18}'
      console.log(this.jsonToStrMap(myMap5))
    },
    jsonToStrMap (jsonStr) {
      return this.objToStrMap(JSON.parse(jsonStr))
    },
    mapToArrayJson (map) {
      return JSON.stringify([...map])
    },
    strMapToJson (strMap) {
      return JSON.stringify(this.strMapToObj(strMap))
    },
    strMapToObj (strMap) {
      let obj = Object.create(null)
      for (let [k, v] of strMap) {
        obj[k] = v
      }
      return obj
    },
    objToStrMap (obj) {
      let strMap = new Map()
      for (let k of Object.keys(obj)) {
        strMap.set(k, obj[k])
      }
      return strMap
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
