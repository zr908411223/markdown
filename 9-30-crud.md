## crud(客户端)操作数据库


  客户端通过不同的request来实现对数据库的crud

  request包括 verb 和 path

  verb { get (获取) , post (写内容) , put (更新) , delete (删除) }


  ### 这就是所谓的rest架构


  - GET /posts      读取所有文章

  - POST /posts     新建一篇文章

  - PUT /posts/:post_id    更新一篇文章

  - GET /posts/:post_id    读取特定的一篇文章

  - DELETE /posts/:post_id    删除一篇文章


  如下：

  ```js

    var express = require('express');
    var app = express();
      app.get('/posts', function(req, res) {
        console.log('get post')
      })
      app.get('/posts:id', function(req, res) {
        console.log('get/posts/:id')
      })
      app.put('/posts/:id', function(req, res) {
        console.log('put /posts/:id')
      })
      app.post('/posts/:id', function(req, res) {
        console.log('post /posts')
      })
      app.delete('/posts/:id', function(req, res) {
        console.log('delete /posts/:id')
      })
      app.listen(3000, function() {
        console.log('run on post 3000')
      })

  ```


  ### express 路由控制  +  mongoose

  1. express 路由

  跑在服务器上，相应客户端发出的request，决定哪部分后台代码要被执行


  2. 使用curl模拟：请求调试 API

  ```

  curl --request PUT localhost:3000/posts/123

  ```

    //123是id（博客页数）

  将``console.log('')``改成``res.send('')``可直观在curl请求中查看到



### 模拟数据请求回应

- 安装rest客户端

  ```
  advanced rest client
  ```

  网址：

    http://pan.baidu.com/s/1c0vUnJi

    密码：z34d

- 安装完毕

  登录：

    http://chrome-extension://

  使用以下代码复制“ ”内部内容到相对应位置

  ```
  http://localhost:3000/posts
  ```
  curl -H "```Content-Type: application/json```" -X POST -d
  '```{"title":"myTitle","content":"myContent"}```'

- 项目内下载body

  "body-parser": "^1.15.2"

  ```
  npm install --save body-parser
  ```



# 什么是API?

1. API是由当前程序提供出来的

2. 提供给另外一个程序的开发者使用的程序接口

3. 作为前端开发者，我们所说的是Web API

  http://en.wikipedia.org/wiki/WebAPI

 ##### API本身就是一个请求   verb + path
