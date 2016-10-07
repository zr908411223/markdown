### 同源策略

1. 报错信息：

  ```
  XMLHttpRequest cannot load
  http://lacalhost:3000/posts.NO
  'Access-Control-Allow-Origin'
  header is present on the requested
  resource

  ```


  - localhost:8080      ————————      localhost:3000
             react          API        Express
       客户端和服务器端域名相同，同时端口也要相同

       原因：github关闭了同源策略


  - HTTP   Request

    HTTP Response


  - HTTP 报头（header）

    Access-Control-Allow-Origin    ————访问权限允许源头

    Access-Control-Allow-Origin   如果后方添加网址，及允许查询该网站报头

    Access-Control-Allow-Origin *   


###### 如何去查看请求报头?

  以github为例

  ```
  curl -I localhost:3000/posts
  ```

### 取消 express 同源限制

1. 服务器端设置 Access-Control-Allow-Origin: *

2. CORS

  Cross Origin resource share
  跨域资源共享

3. 装包   cors

  ```
  npm install --save cors
  ```

  index.js内部添加：代码!

  关闭同源策略，开放 CORS

  ```js
  var cors = require('cors');
  app.use(cors());
  ```

4. 请求查看报头
  连接时，重新开命令行访问
  ```
  curl -I localhost:3000/posts
  ```
