  <template>
    <div class="hello">
    </div>
  </template>

  <script>
  export default {
    methods: {
      ObjectDemo () {
        console.log('对象')
        console.log(this.getPoint())
        //	Object.is用来比较两个值是否严格相等。它与严格比较运算符（===）的行为基本一致
        console.log(Object.is('foo', 'foo'))
        console.log(Object.is({}, {}))
        //	不同之处只有两个：一是+0不等于-0，二是NaN等于自身
        console.log(+0 === -0)
        console.log(NaN === NaN)
        console.log(Object.is(+0, -0))
        console.log(Object.is(NaN, NaN))
        this.objectAssign()
      },
      getPoint () {
      	let x = 1
      	let y = 10
      	return {x, y}
      },
      objectAssign () {
        //	Object.assign方法用来将源对象（source）的所有可枚举属性复制到目标对象（target）
        let target = { a: 1}
        let source1 = { b: 2}
        let source2 = { c: 3}
        Object.assign(target, source1, source2)
        console.log(target)
        console.log('克隆对象')
        let targetYzs = {
          a: 12,
          b: 'yzs',
          c () {
            console.log('你最帅')
          }
        }
        let cloneYzs = Object.assign({}, targetYzs)
        cloneYzs.a = 18
        console.log(cloneYzs)
        console.log(targetYzs)
        //	采用上述方法克隆，只能克隆原始对象自身的值，不能克隆它继承的值。如果想要保持继承链，可以采用下面的代码
        let cloneYzs1 = this.clone(targetYzs)
        console.log(cloneYzs1)
        //	将多个对象合并到某个对象
        //	let merge = (target, ...sources) => Object.assign(target, ...sources)
        //	如果希望合并后返回一个新对象，可以改写上面的函数，对一个空对象合并
        let merge = (...sources) => Object.assign({}, ...sources)
        //	Symbol值可以作为标识符用于对象的属性名，保证不会出现同名的属性
        console.log('Symbol')
        let mySymbol = Symbol()
        let a = {
          [mySymbol]: 'hello'
        }
        console.log(a[mySymbol])
        //	Symbol作为属性名，它不是私有属性，有一个Object.getOwnPropertySymbols方法可以获取指定对象的所有Symbol属性名
        let obj = {}
        let ab = Symbol('ab')
        let bc = Symbol.for('bb')
        obj[ab] = 'Hello'
        obj[bc] = 'World'
        let objectSymbols = Object.getOwnPropertySymbols(obj)
        console.log(objectSymbols)
        this.SymbolFor()
      },
      clone (origin) {
      	let originProto = Object.getPrototypeOf(origin)
      	return Object.assign(Object.create(originProto), origin)
      },
      SymbolFor () {
      	console.log('Symbol.for')
      	//	Symbol.for接受一个字符串作为参数，然后搜索有没有以该参数作为名称的Symbol值。如果有，就返回这个Symbol值，否则就新建并返回一个以该字符串为名称的Symbol值
      	let s1 = Symbol.for('foo')
      	let s2 = Symbol.for('foo')
      	console.log(s1 === s2)
      	//	Symbol.keyFor方法返回一个已登记的Symbol类型值得key
      	console.log(Symbol.keyFor(s1))
        let s3 = Symbol('foo')
        console.log(Symbol.keyFor(s3))
        this.Proxy()
      },
      Proxy () {
      	console.log('Proxy实例')
      	//	new Proxy()表示生成一个Proxy实例，target参数表示所要拦截的目标对象，handler参数也是一个对象，用来定制拦截行为
      	let proxy = new Proxy({}, {
      		get: function(target, property) {
      			return 35;
      		}
      	})
      	console.log(proxy.time)
      	console.log(proxy.name)
      	console.log(proxy.title)
      }
    },
    created () {
      this.ObjectDemo()
    }
  }
  </script>

  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  </style>
