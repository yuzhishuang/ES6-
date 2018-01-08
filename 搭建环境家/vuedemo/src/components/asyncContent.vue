  <template>
    <div class="hello">
    </div>
  </template>

  <script>
  export default {
    methods: {
      generatorDemo () {
        console.log('异步操作和async函数')
        let g = this.gen(1)
        //  console.log(g.next().value)
        g.next()
        g.throw ('出错了')
        console.log('class类')
        let Myclass = class Me {
          getClassName () {
            return Me.name;
          }
        }
        let inst = new Myclass()
        console.log(inst.getClassName())
        //  采用Class表达式，可以写出立即执行的Class
        let person = new class {
          constructor (name) {
            this.name = name
          }
          sayName () {
            console.log(this.name)
          }
        }('张三')
        console.log(person.sayName())
        if (true) {
          var xxx = 123
          console.log(xxx)	
        }
      },
      * gen (x) {
        try {
          var y = yield x + 2
        } catch (e) {
          console.log(e)
        }
        return y
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
