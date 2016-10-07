### 简单的前台后台关系梳理-拆分小案例

注：

实现的功能就是：把客户端的js对象，发送到server服务器端

清晰前台发送请求，后台反馈数据之间的关系和axios的使用

-  创建node.js的新项目

  文件名：`demo-axios-send-data`

  （此案例在digicity-express-api项目下创建）

  文件夹内部命令行中，创建json，执行命令如下：

  `echo {} >package.json`


1. 创建 `前台client` 和 `后台server` 两个文件夹

  将创建的json分别放置到client及server内

2. client、server内创建index.js

  代码如下：

  client-index.js:

  ```js
  var axios = require('axios');
  var data = {
   title: 'myTitle',
   content: 'myContent'
  }
  axios.post('http://localhost:3000/posts', data)
  ```

  server-index.js:

  ```js
  var express = require('express');
  var app = express();
  var bodyParser = require('body-parser');

  app.use(bodyParser.json());
  app.post('/posts', function() {
    console.log(post);
  });
  app.listen(3000, function() {
    console.log('running on port 3000...');
  })
  ```

3. 运行server:

  命令行执行：
  node index.js

  注：提示下载express包：
  `npm i --save express`

  另开命令行执行检测:
  `curl --request POST http://localhost:3000/posts`

  报错：Error:data is not defined
  数据没有被定义

4. 运行client:

  命令行执行：
  node index.js

  注：提示下载axios包：
  `npm i --save axios`

  测试client运行： node index.js 查看server是否接收

5. Error:

  修改后台代码：

  ```js
  var express = require('express');
  var app = express();
  var bodyParser = require('body-parser');
  app.use(bodyParser.json());

  app.post('/posts', function(req. res) {
    console.log(req.body);
  });

  app.listen(3000, function() {
    console.log('running on port 3000...');
  })
  ```

  相关body使用：

  - 安装body-parser包

  - server 引入：

    ```js
      var bodyParser = require('body-parser');
      app.use(bodyParser.json());
    ```

6. 检测：

  - server 重启

  - client 运行 node index.js

  - 查看 server 中的代码是否添加


《 END 》
