# mongoose

一个项目只需要一个数据库就够了，因为一个数据库可以建很多集合，所以数据库名与项目名尽量一致。

1. 什么是mongoose?

  是express代码与mongodb的连接层

2. mongoose的作用

  把数据转化成js对象，不在用mongole-shell操作数据库，以便我们用js代码来操作mongoledb数据库中的数据

3. mongoose的使用

  - 首先必须已经安装node js 与mongodb

  - 在项目中安装mongoose

    ```
    $npm install --save mongoose

    ```

  - 在项目中只能够创建一个数据库连接，如下：

    ```js

    var mongoose = require('mongoose');
    //引用mongoose模块
    var db = mongoose.createConnection
    ('localhost','test');//创建一个数据库连接

    ```

  - 打开本机localhost的test数据库时，我们可以监测是否有异常

    ```js

    db.on('error',console.error.bind
    (console,'连接错误:'));
    db.once('open',function(){
     //一次打开记录
    });

    ```
    注意：成功开启数据库后，就可以执行数据库相应操作，假设以下代码都在回调中处理

  - 定义一个Schema

    描述数据记录的结构，规定数据记录中的字段名称及字段的数据类型

    ```js

    var catSchema = mongoose.Schema({
      name: String
    });

    ```

  - 将该Schema发布为Model

    了解Model的概念

    ```js

    var cat = mongoose.model
    ('cat',catSchema);

    ```

    第一个参数：模型对应的集合名称的单数

    第二个参数：一条数据记录的结构

    http://mongoosejs.com/docs/models.html

  - 用Model创建Entity

    ```js

    var Kitty = new cat({
      name: 'HelloKitty'
    });
    console.log(Kitty.name);

    ```

  - 将所创建的Entity进行保存（储存数据记录）

4. 用js代码进行增删改查

  - 异步执行

     ```js

     Info.find().exec(function(err, users) {
       // 异步执行
     console.log(users);

     ```

   - 删除延迟错误提醒（无用垃圾）-在atom上方添加如下：

     ```
     mongoose.Promise = global.Promise;
     ```
