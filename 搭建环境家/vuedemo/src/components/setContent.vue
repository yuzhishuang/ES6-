  <template>
    <div class="hello">
    </div>
  </template>

  <script>
  export default {
    methods: {
      setDemo () {
        console.log('set')
        //  Set它类似于数组，但是成员的值都是唯一的，没有重复的值。Set本身是一个构造函数，用来生成Set数据结构
        //  let s = new Set()
        //  [2, 3, 4, 5, 2, 2].map(x => s.add(x))
        //  for (i of s) {console.log(i)}
        let items = new Set([1, 2, 3, 4, 5, 5, 5])
        console.log(items.size)
        let set = new Set()
        set.add({})
        console.log(set.size)
        set.add({})
        console.log(set.size)
        //  判断是否包括一个键上Object结构和Set结构的写法不同
        //  对象写法
        let properties = {
          width: 1,
          height: 2
        }
        let width = 'width'
        if (properties[width]) {
          console.log('对象动作')
        }
        //  Set的写法
        let properties1 = new Set()
        properties1.add("width")
        properties1.add("height")
        if (properties1.has('width')) {
          console.log('Set结构')
        }
        //  Array.from方法可以将Set结构转为数组
        let items1 = new Set([1, 2, 3, 4, 5, 4])
        let array = Array.from(items1)
        console.log(array)
        let array1 = [2, 3, 4, 2, 3, 4]
        let fanhui = this.dedupe(array1)
        console.log(fanhui)
        //  Set可以很容易地实现并集，交集和差集
        let a = new Set([1, 2, 3])
        let b = new Set([4, 3, 2])
        //  并集
        let union = new Set([...a,...b])
        //  交集
        let intersect = new Set([...a].filter(x => b.has(x)))
        //  差集
        let difference = new Set([...a].filter(x => !b.has(x)))
      },
      //  去除数组重复的方法
      dedupe (array) {
        return Array.from(new Set(array))
      }
    },
    created () {
      this.setDemo()
    }
  }
  </script>

  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  </style>
