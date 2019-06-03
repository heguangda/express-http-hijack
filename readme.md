#这是一个基于 express 的请求与响应非阻塞拦截

``` js
 let express = require('express')
 let httphijack = require('httpjack')

  //拦截请求后做的事情
 function reqPre(){
  db.insert() //类DB插入操作，不阻塞原请求
 }
 function resPre(){
  db.update() //DB更新操作，不阻塞原请求
 }
 let midware = function(req, res, next){
   httphijack(req, res, reqPre, resPre)
   next()
 }

let app = express()
app.use(midware)

```