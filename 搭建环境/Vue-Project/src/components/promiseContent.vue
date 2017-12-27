<template>
  <div id = 'Promise'>
    Promise对象
  </div>   
</template>

<script>
export default {
  name: 'setContent',
  methods: {
    demo () {
      console.log('Promise对象')
      //  Promise就是一个对象，用来传递异步操作的消息
      //  下面代码，timeout方法返回一个Promise实例，表示一段时间以后才会发生的结果。过了指定时间（ms参数）以后，Promise实例的状态变为Resolved，就会触发then方法绑定的回调函数
      this.timeout(2000).then((value) => {
        console.log(value)
      })
    },
    timeout (ms) {
      return new Promise((resolve, reject) => {
        setTimeout(resolve, ms, 'done')
      })
    },
    //  异步加载图片的例子
    loadImageAsync (url) {
      return new Promise((resolve, reject) => {
        var image = new Image()
        image.onload = function () {
          resolve(image)
        }
        image.onerror = function () {
          reject(new Error('Could not load image at' + url))
        }
        image.src = url
      })
    },
    //  用Promise对象实现的AJAX操作的例子
    getJSON (url) {
      let promise = new Promise((resolve, reject) => {
        let client = new XMLHttpRequest()
        client.open('GET', url)
        client.onreadystatechange = handler
        client.responseType = 'json'
        client.setRequestHeader('Accept', 'application/json')
        client.send()
        function handler () {
          if (this.readyState !== 4) {
            return
          }
          if (this.status === 200) {
            resolve(this.response)
          } else {
            reject(new Error(this.statusText))
          }
        }
      })
      return promise
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
