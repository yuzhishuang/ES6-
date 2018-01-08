  <template>
    <div class="hello">
    </div>
  </template>

  <script>
  export default {
    methods: {
      generatorDemo () {
       console.log('编码风格')
       //  函数的参数如果是对象的成员，优先使用解构赋值
       let obj = {
         firstName: 'yzs',
         age: 12
       }
       this.getFullName(obj)
       //  如果函数返回多个值，优先使用对象的解构赋值，而不是数组的解构赋值。这样便于以后添加返回值，以及更改返回值的顺序
       const {left, right} = this.processInput()
       console.log(left, right)
      },
      getFullName (obj) {
         const {age, firstName} = obj
         console.log(firstName, age)
      },
      processInput () {
        let left = 1
        let right = 2
        let top = 3
        let bottom = 4
        return {left, right, top, bottom}
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
