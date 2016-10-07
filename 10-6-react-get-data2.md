### 客户端得到data


1.搭建react基本开发环境

Webpack:

- ES6 模块，打包成一个 `bundle.js`

- 负责开发环境的基础设施 `dev-server` 负责编译出产品代码

Babel:

- 提供 ES6 转换成 ES5  （ES6.>ES5）

- React 的 jsx 用 babel 来编译成js


 2.App.js代码:

  ```js
  import React from 'react';
  class App extends React.Component {
    handleSubmit(e) {
      e.preventDefault();
      let title = this.refs.title.value;
      let content = this.refs.content.value;
      let data = {title,content}
      console.log(data);
      // { title: 'hello', content: 'xxx'}
    }
    render () {
      return(
        <div>
          <form onSubmit={this.handleSubmit.bind(this)}>
            <input type='text' ref='title' /><br />
            <input type='text' ref='content' /><br />
            <input type='submit' />
          </form>
        </div>
      )
    }
  }
  export default App;
  ```

### 用mongodb 操作数据库的基本操作

  http://haoqicat.com/react-express-api/2-mongodb

  mongodb逻辑：

  - 启动

  `mongod --dbpath=./data`

  - 打开mongodb的命令行（另起服务器）

  `mongo`

  - 创建/打开文件夹

  `use digicity-express-api`

  - 创建一个collection

  `db.createCollection('posts')`

  - 查看库

  `show collections`

  - 插入操作

  `db.posts.insert({title:'hello'})`

  - 查看博客

  `db.posts.find()`

  详见链接
