# react-demo
### 1.React简介

- React起源于Facebook内部项目，因为该公司对市场上所有的javascript的mvc框架都不满意，就决定自己写一套，用来架设Instagram的网站，做出来之后，发现很好用，就在2013年5月开源了。

- Angular 2009年出来的 谷歌出来的 MVC不支持组件化开发

- 由于React的设计思想独特，属于革命性创新，代码逻辑非常强，所以很多人都在使用

- 清楚两个概念：

  - library(库): 小而巧，

     库的优点是 每个库之前的API都很类似，所以从一个库切换到另外一个库的时候会比较好切换

    

  - Framework（框架）：大而全的是框架

​             框架提供了一整套的解决方法，就跟360全家桶一样，不管是什么功能都能。

​			每个框架用的方法和API甚至语法都不一样，所以如果一个项目想从一个框架迁移到另外一个框架是非常麻    			烦的一件事情，估计全部都要改

### 2.React与vue的对比

#### 组件化

- 什么是模块化

  - 是从**代码**的角度进行分析
  - 把一些可复用的代码抽离为单个的模块，便于项目的维护和开发（虽然一开始的时候是每天都在写不一样的单独的模块，但是在开发到中后期的时候，很多功能都一样的时候，这时候就直接调用之前的写好的默模块就好了）
  - Node里面就有很多第三方模块来供我们使用

- 什么是组件化

  - 是从**UI界面**的角度进行分析
  - 把一些可复用的UI元素抽离为单独的组件，便于项目的维护和开发

- 组件化的好处

  - 随着项目规模的增大，手里的组件越来越多，这样子遇到相同的UI界面功能的时候，就能直接拿起来用

- Vue是如何实现组件化的

  - 在vue里面用的最多的是.vue的文件来创建对应的文件，里面又分三大结构：

    ```js
    template   页面结构
      
    script	操作页面中空控件的行为
    
    style 页面中渲染的样式
    # 需要注意的是，使用.vue 文件的时候，需要用 webpack来进行编译
    # .vue 文件需要用到vue-loader 这个插件来进行编译 loder就是将这三个结构编译整合起来
    # 所以使用 import Home from './Home.vue'  中的Home其实是别人编译后的结果
    ```

- React是如何实现组件化的

  - 需要注意的是，React中有组件化的概念。但是，并没有像vue这样的组件模板文件
  - React中。一切都是JS来表现的，就像vue中是通过模板文件，但是react中这三个部分都是通过js来实现的，因此要学习react,js要合格，ES6和ES7 (async  和 await)要会用

#### 开发团队

- React是Facebook前端开发团队来进行维护的，因此，React的维护开发团队，技术实力强
- Vue第一版是作者自己开发的。第二版有个开源小团队，进行相关的开发和维护

#### 社区方面

- 在社区方面，React由于诞生的比较早，所以社区比较强大，一些常见的问题、坑、最优解决方案、文档、博客，在社区都可以很方便的就能找到
- Vue是近两年才火起来的，所以，它的社区相对于react来说，更小一些，可能有的一些坑，没人踩过

#### 移动App开发体验方面

- React,综合ReactNative(**学习ReactNative的前提是必须先学好React**). 也提供了无缝迁移到移动App的开发体验（RN用的最多，也是最火最流行的） => 这个reactNative是国内国外大企业在用

- Vue， 综合Weex这门技术，提供了迁移到移动端App开发的体验（Weex，目前只是一个小的玩具，并没有很成功的案例）=> Weex都是阿里自己在用

### 3.为什么要学习React

- 和Angular1相比，React设计的很优秀，一切基于JS并且实现了组件化开发的思想
- 开发团队很强悍，不必担心断更的情况
- 社区强大，很多问题都能找到对应的解决方案
- 提供了无缝转到ReactNative上的开发体验，让我们技术能力得到了扩展体验，增强了我们的核心竞争力
- 很多企业上，前端项目的技术选型采用的是React.js

### 4.React中几个核心的概念

```js
一个例子：
需求： 点击列头，实现对应表格数据的排序

1.表格中的数据从哪儿来？
  + 从数据库查询回来的
2.这些查询到的数据，存放到哪儿？
  + 这些数据在浏览器中的内存 （localStorage）中存放着，而且是以 对象数组 的形式来表现
3.这些数据，是怎么渲染到页面上？
  + 方案1： 手动for循环整个数组，然后手动拼接字符串 str += '<str></str>'
  + 方案2； 使用模板引擎，art-template

4.思考：上述的方案，有没有性能上的问题？

5.如果客户点击按钮，想要实现时间从大到小排序：
	+ 1.用户触发点击事件，在事件中，浏览器把内存中的对象数组重新排序
  + 2.当排完序之后，页面是旧的；  但是内存中的对象数组是新的
  + 3.想办法，把最新的数组重新渲染到页面上去  #这里把最新的数组渲染到页面上去是不是有性能上的问题
  
6.分析与总结：上述方案中，只是实现了把数据渲染到页面上的能力，但是并没有把性能做到最优
7.#如何才能把性能做到最优：按需渲染页面（只是重新渲染更新的数据所对应的页面元素）

8.问题是如何实现页面上的按需更新？
 + 获取内存中的新旧两个DOM树，进行对比，得到 需要按需更新的DOM元素
 
9.如何获取新旧DOM树，从而实现DOM树的对比？
 + 分析： 浏览器并没有给我们提供获取新旧DOM树的API，因此，我们没有办法拿到浏览器内存中的DOM树
 + 但是程序员是不会认输的！！！
 + 程序员可以手动更新模拟两颗DOM树

10.程序员怎么手动模拟两颗DOM树？？？？
 + 首先模拟一个元素标签
   <div id="mydiv" title="说实话" data-index="0">
     我好漂亮 
		 <p>哈哈</p>
   </div>
	 JS对象模拟DOM树如下：
   var div = {
     tagName: 'div',
     attrs: {
       id: 'mydiv',
       title: '说实话',  
       ‘data-index’: "0"
     }，
     childrens: [
     	'我好漂亮',  => 如果这里的数据变成了`我现在变丑了`，那么根据对比，浏览器只需要重新渲染这句话就好了
       {
     		 tagName: 'p',
     		 attrs: {},
       	 childrens: [
           "哈哈" 
         ]
       }
     ]
   }
   
   
 11.# 程序员手动模拟的这两颗新旧DOM树，就是react中的虚拟DOM的概念
   + 所以虚拟DOM就是用JS对象的形式 ， 模拟页面上的DOM嵌套关系的

#总结：虚拟DOM 是以 JS对象 的形式存在的
 
```

#### DOM树的概念

- 一个页面呈现的过程：
  - 1.浏览器请求服务器获取页面HTML代码
  - 2.浏览器要在内存中，解析DOM结构，并在浏览器内存中，渲染出一颗DOM树
  - 3.浏览器把DOM树呈现到页面上

####  虚拟DOM

- 虚拟DOM的全称是Virtual Document Object Model

####  DOM的本质是什么

- 浏览器中的概念，用JS对象来表示页面中的元素，并提供了操作DOM对象的API

#### 什么是React中的虚拟DOM

- 虚拟DOM是框架的概念

- 用程序员使用JS对象来表示页面中的DOM和DOM嵌套
- 本质是：用JS对象来模拟DOM元素和嵌套关系
- 目的是：为了实现页面元素的搞笑更新

#### 为什么要实现虚拟DOM

- 为了实现页面中，DOM元素的高效更新

#### DOM和虚拟DOM的区别

- DOM

  - 是浏览器中提供的概念

  - 使用JS对象，表示页面上的元素，并提供了操作元素的API

- 虚拟DOM

  - 是框架中的概念
  - 是开发程序员因为浏览器没有提供先关的API而手使用JS对象模拟的DOM

#### Diff算法

- tree diff: 新旧两颗DOM树，逐层对比的过程，就是Tree Diff; 当整颗DOM逐层对比完毕，则所有需要被按需更新的元素，必然能够找到
- component diff: 
  - 在进行Tree Diff的时候，每一层中，组件级别的对比，叫做component Diff
  - 如果对比前后，组件的类型相同，则暂时认为此组件不需要更新
  - 如果对比前后，组件类型不同，则需要移除旧组件，创建新组件，并追加到页面上

- Element diff: 在进行组件对比的时候，如果两个组件类型相同，则需要进行元素级别的对比，这叫做ELement diff

### 5.创建基本的webpack4.x项目

##### 创建基本的项目骨架

- 运行`npm init -y`初始化一个项目

- 新建一个src文件，所有项目源代码都放进src

  - 在这个文件夹下面，创建index.html文件
  - 创建main.js文件，main.js是webpack入口文件,要想实现打包

- 新建一个dist文件，项目做好之后发布产品，最终发布版本是放在dist文件里面

- 输入`npm i webpack webpack-cli -d`安装webpack 

  - webpack 4.x以上的需要安装webpack-cli ， webpack-cli是脚手架，命令行工具

  - webpack 3.6是把打包工具和命令行工具放在一起的
  - webapck4.x的版本是将打包工具和命令行分开了

##### 设置webpack基本配置

- 这个时候在终端输入`webpack`会提示下面一句话

  ```js
  WARNING in configuration
  The 'mode' option has not been set, webpack will fallback to 'production' for this value. Set 'mode' option to 'development' or 'production' to enable defaults for each environment.
  You can also set it to 'none' to disable any default behavior. Learn more: https://webpack.js.org/configuration/mode/
  
  # 意思是需要配置mode选项，选择是development或者production
  ```

- 按照官网提示是 在文件夹根目录下面创建一个`webpack.config.js`的文件，在里面写入下面的代码：

  ```js
  //向外暴露一个打包的配置对象  因为webpack是基于Node构建的，所以webpack支持所有NodeAPI和语法
  
  module.exports = {
    mode: 'development'
    
  
  }
  ```

- 写入上面的代码，再在控制台输入`webpack`,还是在报错：

  ```js
  ERROR in Entry module not found: Error: Can't resolve './src' in '/Users/fuzhiqun/Desktop/01-webpack-base'
  #意思是 没有在 ./src 路径下 找到 模块的入口文件
  #但是实际上我们是有的，但是wenpack没有找到
  
  // 在webpack4.x中，有一个很大的特性，就是约定大于配置，约定了默认的打包入口路径是 src => index.js
  ```

- 所以将`main.js` 文件名 改为`index.js `再次执行`webpack`, 就会提示打包成功

- 在dist目录下面就会出现一个mian.js，里面就是我们写的那些代码

  ```js
  mode: 'development'
  # 如果选择 development 模式， 那么webpack打包的dist目录下的main.js是不会压缩的
  mode: 'production'
  # 如果选择 production 模式, 那么webpack打包的dist目录下的main.js是压缩的，体积会变得特别小
  ```

- 需要注意的是： webpack4.x提供了约定大于配置的概念，目的是为了尽量减少配置文件的体积

  - 默认约定了：

  - 打包de的入口文件是：`src` => `index.js`

  - 打包的输出文件是`dist` => `main.js`

    

- 在`webpack.config.js`， 不能使用`export default`来导出对象，因为这是ES6中向外导出模块的API，与之对应的是 `import ** from '标识符'`
- 题外话： 哪些特性Node支持呢？ 如果chrome浏览器支持哪些，那Node就支持哪些

##### 配置实时的打包编译

-  控制台安装`npm i webpack-dev-server -D `

- 安装完后打开`package.json`, 在`script`里面，加入` "dev": "webpack-dev-server"`并保存

- 在控制台输入`npm run dev`,会弹出很多信息，最后显示`｢wdm｣: Compiled successfully.`表示编译成功

  ```js
  > webpack-dev-server
  
  ℹ ｢wds｣: Project is running at http://localhost:8080/
  # 项目运行在  http://localhost:8080/ 上面 点击打开这个网址，会发现其实是根目录中间的文件
  # 输出的main.js是在根路径 在http://localhost:8080/加上main.js ，会发现main.js的源代码
  
  
  ℹ ｢wds｣: webpack output is served from /
  # webpack输出是从根目录上输出的
  ℹ ｢wds｣: Content not from webpack is served from /Users/fuzhiqun/Desktop/01-webpack-base
  
  ℹ ｢wdm｣: Hash: f42483b796ea2e8c1641
  
  Version: webpack 4.41.1
  Time: 615ms
  Built at: 2019-10-15 12:00:21 PM
    Asset     Size  Chunks             Chunk Names
  main.js  360 KiB    main  [emitted]  main
  Entrypoint main = main.js 
  
  [./src/index.js] 61 bytes {main} [built]
      + 18 hidden modules
  ℹ ｢wdm｣: Compiled successfully. # 有这句话表示编译成功
  
  ```

- 这边需要注意的是：`webpack-dev-server`打包好的 `main.js`是 托管到了内存中，所以在项目文件夹中是看不到的，但是，我们知道，在项目根目录中，有一个看不见的`main.js`文件，所以我们应该在`index.html`文件中，把引入的main.js的路径改一下，改成访问内存中的main.js:

  ```js
    <script src="../dist/main.js"></script>
    改为👇：
    <script src="/main.js"></script>
  ```

  

##### 配置打包好之后自动打开浏览器

- 在`package.json文件中，找到之前设置过后的`"dev": "webpack-dev-server"` 这一行，在后面继续设置，写下如下代码:

  ```js
  #  --open 是指默认打开浏览器  
  #  --port 3000 指的是默认打开3000端口
  #  --host 127.0.01 指的是通过127.0.0.1打开 不是通过localhost 
  
  "dev": "webpack-dev-server --open --port 3000 --hot --host 127.0.0.1"
  
  # 如果想要通过IE 或者 火狐启动浏览器 可以在--open后面设置浏览器的名称 这样就可以直接打开你想要的浏览器
  ```

##### 把首页也放到内存中去

- Webpack-dev-server  将 main.js 放在了内存中，这样子就能快速打开和读取，我们应该也将首页放在物理磁盘中去，但是这样我们就需要弄外一个插件`html-webpack-plugin`,它可以帮我们把页面生存到内存中去

- 使用命令： `npm install html-webpack-plugin -D  `

- 安装好之后，在`webpack.config.js`中加入以下代码：

  ```js
  const path = require('path') //因为要使用路径，所以必须将路径模块导入进来
  const HtmlWebPackPlugin = require('html-webpack-plugin')  //导入在内存中自动生成的html页面的插件
  //创建一个插件的实例对象
  const htmlPlugin = new HtmlWebPackPlugin({
    template:  path.join(__dirname, './src/index.html'),   //源文件
    filename:  'index.html'     //生成的内存中首页的名称
  })
  
  module.exports = {
    mode: 'development',
    plugins: [ 
      htmlPlugin  # 将上面创建的实例对象放入这个 plugins 中
    ]
  }
  ```

- 注意: 再次使用`npm run dev`这个命令，就可以自动打开首页，但是实际上项目文件夹中并么有index.html这个文件，说明 ，`html-webpack-plugin `这个插件已经将文件放入到了内存中，打开首页，查看源代码，会发现在body里面，多出来了一个script标签：

  ```js
  <body>
    <h1>这是首页</h1>
  # 这个script标签是自动生成加上去的 因为html-webpack-plugin这个插件会自动把打包好的文件追加上去，就不用自己去写了，因为它帮我们追加的，它会自己处理好这个路径
  
  # 然后我们就可以把 index.html 文件中的 手动引入的main.js 给删除了
  <script type="text/javascript" src="main.js"></script>
  </body>
  ```

- 总结：一个是帮我们在内存中生成打包好的js文件，一个是帮我们在内存中生成首页并自动把打包好的文件注入到html里面去，到此为止，我们已经将基本的webpack文件设置好了

##### 配置babel

- 安装`babel`插件 ** 需要注意的是安装的都是最新版的**

  - 运行`npm i @babel/core @babel/preset-env @babel/runtime @babel/plugin-transform-runtime @babel/plugin-proposal-class-properties @babel/preset-react -D` 

  - 运行`npm install babel-loader`

- 能够识别转换jsx语法的包`babel-preset-react`
  - 运行`npm i babel-preset-react -D`

- 添加`.babelrc`配置文件

  ```js
  {
    "presets":["@babel/preset-env","@babel/preset-react"], 
    "plugins":["@babel/transform-runtime","@babel/plugin-proposal-class-properties"]
  }
  ```

- 在`webpack.config.js`中设置babel-loader

  ```js
  module.exports = {
    mode: 'development',
    plugins: [ 
      htmlPlugin  
    ],
    module: {
      rules: [
        {
          test: /\.m?js$/,
          exclude: /(node_modules|bower_components)/,
          use: {
            loader: 'babel-loader',
            options: {
              presets: ['@babel/preset-env']
            }
          }
        }
      ]
    }
  }
  ```

- 经过上面步骤babel就配置好了

### 7.在项目中使用react

##### 安装依赖包

- 运行`npm i react react-dom -S`安装包
  - react:  专门用于创建组件和虚拟DOM的，同时组件的生命周期都在这个包里
  - React-dom: 专门用来进行DOM操作的，最主要的应用场景是`ReactDOM.render()`

##### 创建基本的react结构

- 在`index.html`页面中，创建容器：

  ```html
  <body>
   <!-- 创建一个容器，将来，渲染的虚拟DOM，会放到容器内显示 -->
   <div id="app"></div>
  </body> 
  ```

  在`index.js`中，一共三步：

  ```js
  # 第一步： 导入两个包
  import React from 'react'  //创建组件、虚拟DOM元素、生命周期
  import ReactDOM from 'react-dom'  //把创建好的组件和虚拟DOM渲染到页面上
  
  
  #第二步：创建虚拟DOM元素（注意:这个是在内存中）
  const myh1 = React.createElement('h1', null , '这是一个h1标签')
  //需要注意的是：React.createElement里面至少接收三个参数；
  //参数一：创建的元素的类型，字符串，表示元素的名称
  //参数二：是一个对象或者null，表示这个DOM元素的属性
  //参数三：子节点（包括其他虚拟DOM 获取文本子节点）
  //参数n: 其他子节点
  
  #第三步：使用ReactDOM 把 虚拟DOM 渲染到页面上
  ReactDOM.render( myh1 , document.getElementById('app'))
  //需要注意的是 ReactDOM.render里面接收两个参数
  //第一个参数： 要渲染的虚拟DOM的元素
  //第二个参数:  指定页面上的容器  =>就是在index.html中的创建的容器
  
  ```

- 用上面方式创建虚拟DOM元素创建一个元素还好，但是要是创建多个呢？

  ```js
  import React from 'react'   
  import ReactDOM from 'react-dom'  
  
  const myh1 = React.createElement('h1', null , '这是一个h1标签')
  const mydiv = React.createElement('div',null , '这是一个div元素', myh1) #这样就实现了元素的嵌套
  # 如果接下去还有元素需要嵌套怎么？
  
  # 要知道渲染页面上的DOM结构，最好的方式就是写HTML代码
  # 但是JS文件是不允许写html代码的
  
  ReactDOM.render( mydiv , document.getElementById('app'))
  
  ```

### 8.配置babel解析JSX语法

- 创建基本的react文件

  - 导入包

    ```js
    import React from 'react'
    import ReactDOM from 'react-dom'
    ```

  - 创建虚拟的DOM元素

    ```js
    const mydiv = React.createElement('div', {id: 'mydiv', title: 'div aaa'}, 'div元素')
    ```

  - 调用render函数渲染

    ```js
    ReactDOM.render(mydiv, document.getElementById('app'))
    ```

- 在创建虚拟的DOM元素的过程中，如果使用`React.createElement` 这个来创建是非常麻烦的，特别是要创建多个元素。我们可以采用一种直接在js文件中写入HTML格式的语法。

- 在JS文件中混合写入类似于HTML的语法叫做JSX的语法，符合XML的规范的JS,但是在JS文件里面是默认不能写这种类似于HTML的标记，否则，标记会失败

- 所以如果想要在js文件里面写html格式的文件，需要通过babel转译，具体配置方式，参考配置babel里面的方法

  ```js
  # 需要注意的是：JSX语法的本质是在运行的时候，被转化成了React.createElement形式来执行
  const mydiv = <div id="mydiv" title="div aa">这是一个div元素</div>
  ```

  如果在面试中被问到`jsx是直接把HTML页面中调到页面中去显示吗？`

  这个时候一定要回答`不！！`, 是通过babel转译为`React.createElement`才在页面中显示的

  

#### 9.JSX语法

- JSX语法的本质是： 并不是直接将jsx渲染到页面上，而是在内部转换成了createElement形式再渲染的

- 在jsx中混合写入js表达式： 

  - 在jsx语法中，要把js代码写到{}中

  - 在{}中可以写 `数字`  , `字符串`，`布尔值`，`为属性绑定值` , `渲染jsx元素`，`渲染jsx元素为数组`

    ```js
    import React from 'react'   
    import ReactDOM from 'react-dom'  
    
    let a = 10    # 数字
    let str = '你好，中国'   #字符串 
    let boo = false    #布尔值
    let title = '999'  # 为属性绑定值
    const h1 = <h1>红红火火恍恍惚惚</h1> # 渲染jsx元素，将这个标签想象成一个对象
    const h2 = <h2>你在说什么，我还要装模作样听多久</h2>
    const arr = [     #数组
      <h2>这是👌</h2>,
      <h3>这是👌</h3>
    ]
    
    ReactDOM.render(
    <div>
      { a + 2 }  # 写数字
      {str} # 字符串
      {boo ? '条件为真': '条件为假'} # 布尔值
      
      <p title={title}>这是p标签</p>  #为属性绑定值 直接将属性名称放在{}中
    
      {h1} #渲染jsx元素时，将jsx元素想象成一个对象，所以直接将对象丢入到大括号中间就可以正常显示了
      {h2}
    
      {arr} # 渲染数组 同样也是数组直接放在大括号中
    </div> 
    
    , document.getElementById('app'))
    
    // 什么时候需要{}呢？ 当我们需要在 JSX 控制的区域内，写JS表达式了， 则需要把JS代码写到{}中
    
    ```

  - 将普通字符串数组，转为js数组并渲染到页面上

    ```js
    const arrStr = ['毛利兰'，'柯蓝'，'小五郎'，'灰原哀']
    
    # 需要注意的是map函数是执行一个操作返回一个新的数组 
    {arrStr.map(item =>  <h1>{item}</h1>)}
    ```

    



#### 1.react基本语法

##### vue 和 react 中key的作用

- 如果vue中使用v-for循环 ， 或者在react中使用map来循环的时候，如果需要保持状态（比如这项被选中或者怎么样），最好提供了一个key, 不然状态会紊乱 , 还有就是vue中使用动画的时候也必须加上key，所以为了统一，使用v-for的时候不管是什么状态都必须加key,所以react也需要加key
- 注意： React中需要把key添加给 被forEach 或 map 或 for循环  直接控制的元素

```js
const arrStr = ['毛利兰', '柯蓝' , '小五郎', '灰原哀']

{arrStr.map(item =>  <div  key={item}><h1>{item}</h1></div>)}


# 需要注意的是 如果不加key 会报如下错误：

react.development.js:175 Warning: Each child in a list should have a unique "key" prop.
# 意思是需要给div这个父元素加一个独特的key用来辨识
Check the top-level render call using <div>. See https://fb.me/react-warning-keys for more information. in div
```

##### jsx里面怎么写注释

```
{/* {arr} */} # 推荐使用这个注释 只用占据一行

{
  //这是注释，你看不见我   #这种方法的注释占据的行数太多不推荐
}
```

##### jsx的其他注意事项

- 在JSX创建DOM的时候，所有的节点，必须使用唯一的根元素进行包裹

- 在JSX语法中，标签必须成对出现，如果是单标签，则必须自闭和

- 特别需要注意的是**为jsx中的元素添加类名**需要使用`className`,否则会报这个错

  ```js
  <p class="myele">测试元素内部的属性</p>
  
  # 报错的意思是非法的DOM属性class，你的意思是className？
  react-dom.development.js:558 Warning: Invalid DOM property `class`. Did you mean `className`?
      in p
      in div
  
  # 所以我们为了防止这个错误，应该手动将 class 手写成 className 就不会报错了
   <p className="myele">测试元素内部的属性</p>
  ```

- 同样的**label里面的for属性**也是这个情况

  ```js
  <label for="ooo"></label>
  # 如果像上面这样写，那么就会👇的报错
  react-dom.development.js:558 Warning: Invalid DOM property `for`. Did you mean `htmlFor`?
      in label
      in div
  
  # 为了防止这个错误，我们应该将for 手写成 htmlFor 属性 就不会报错了
   <label htmlFor="ooo"></label>
  ```

  

#### 2.react创建组件的方式一（构造函数）

##### 使用构造函数

- 构造函数里面必须要向外return一个合法的JSX创建的虚拟DOM
- 如果要接收外界传递的数据，需要在构造函数的参数列表中使用props来接收
- 基本的创建方法

```jsx
function Hello (){}  #使用构造函数创建一个组件

ReactDOM.render( 
  <div>
    <Hello></Hello>  # 直接将组价的名称以标签的形式放入到这里就可以
  </div> , 
  document.getElementById('app')
)

```

- 构造函数的注意事项

```jsx
function Hello (){
  return <div>这是一个div组件</div>  # 构造函数里面必须返回一个合法的JSX虚拟的DOM元素
}  
```

#### 3.给组件传递数据的方式

##### 直接将对象的属性传值 

```jsx
function Hello (){
  return <div>这是一个div组件</div>
}   

const dog = {  # 可以直接将这个对象的属性传值给下面的标签里面   
  name: '大黄'，
  age: '10',
  gender: '雄性'
}

ReactDOM.render( 
  <div>
    # 这是直接将对象里面的属性传值给这个组件里面
    <Hello name={ dog.name }  age={ dog.age }  gender={ dog.gender }></Hello> 
    # 如果想传递全部的dog对象，那么使用展开运算符也可以全部展开这个对象
    <Hello {...dog}></Hello>
  </div> ,  
  document.getElementById('app')
)
```



##### 通过构造函数的形参传值

```jsx
function Hello ( props ){ # 通过props传值
	console.log(props) #console.log出一个对象 说明props是个对象 
  return <div>这是一个div组件 -- {props.name} -- {props.age} -- {props.gender}</div>
}   

const dog = {  # 将这个对象直接传给构造函数
  name: '大黄'，
  age: '10',
  gender: '雄性'
}

ReactDOM.render( 
  <div>
    //使用组件为组件传递 props数据
    <Hello name={ dog.name } age={dog.age} gender={dog.gender}></Hello>   
    
  </div> ,  
  document.getElementById('app')
)

```

- 总结:组件接受外界传值：

  - 怎么传值：直接使用使用传值

  - 怎么使用：先用`props`形参接收，然后直接就可以点出来了

    ```jsx
    function Hello ( props ){  
    props.name = 'zs'  #如果在这里更改对象的属性会报错
    console.log(props) 
    return <div>这是一个div组件 -- {props.name} -- {props.age} -- {props.gender}</div>
    }  
    ```

  # 报错信息如下：

  Uncaught TypeError: Cannot assign to read only property 'name' of object '#<Object>'
  未捕获的类型错误:无法分配对象'#<对象>'的只读属性'name'
  react-dom.development.js:21704 The above error occurred in the <Hello> component:
      in Hello
      in div
  上述错误发生在组件:在Hello在div

  # 根据报错信息可以知道  props 是只读的 ， 在vue中的props是用数组接收的 也是只读的

  # 结论：不论是vue还是react,组件中的 props 永远都是只读的，不能被重新赋值

  ```
  
  ```

- 如果将构造函数的首字母小写会怎样？

  ```jsx
  function hello(props){  #如果将构造函数的首字母小写那么会报错
     return <div>这是Hello组件</div>
  }
  ReactDOM.render( 
  <div>
    <hello></hello>
  </div>, 
  document.getElementById('app')
  )
  
  # 报错信息：
  react-dom.development.js:558 Warning: The tag <hello> is unrecognized(不被认可的) in this browser. If you meant to render a React component, start its name with an uppercase letter.
      in hello
      in div
  
  # 不管是在React 还是 Vue， 组件的首字母都是大写的
  ```

#### 4.将组件抽离为单独的文件

##### 处理报错

- 在`src`中创建`components`组件文件夹，在这个文件夹下创建各种单个组件文件，只是将创建的组件放入到这个文件中

  ```jsx
  # components 创建的 Hello.js 文件
  
  //使用es6暴露组件的方式将 Hello 组件暴露出去
  export default function Hello(props){
    return <div>这是Hello组件 -- {props.name} -- {props.age} -- {props.gender}</div>
  }
  
  # 在index.js文件中接收
  import Hello from './components/Hello' 
  ```

- 经过上面两步之后出现报错：`Hello.js:4 Uncaught ReferenceError: React is not defined`,意思是没有发现React

  ```js
  分析：
  在components 创建的 Hello.js文件 我们只是放入了一个 构造函数创建的组件 
  但是我们创建的React组件是必须依赖 react的包 但是在 新创建的组件文件中 我们并没有导入react的包
  
  # 所以必须在单独的组件文件夹里面导入react文件
  import React from 'react'
  ```

##### 配置webpack中@为项目根目录

- 在index.js文件中导入组件的时候，`import Hello from './components/Hello'`，其中的`.`可以变成`@` ，但是需要配置，配置方法是 打开`webpack.config.js`文件，将`module`折叠起来，在下面加一个`alias`，写下如下的代码：

  ```js
  resolve: {
      alias: {   => alias 别名
        '@': path.join(__dirname, './src') //这样设置之后，@就表示项目根目录中src的这一层目录
      }
    }
  ```

- 然后就可以在项目中使用@符号来表示根目录了

  ```js
  // 注意：这里的@符号，表示项目根目录中的src的这一层目录
  import Hello from '@/components/Hello'
  ```

  

#### 5.react创建组件的方式二（class关键字）：

##### class的基本用法

- 定义一个类的方法可以通过构造函数的方式

  ```js
  function Person (){}
  let p1 = new Person() //Person{}
  ```

  

- 同样，在es6里面可以通过class定义一个类

  ```js
  class Animal {}
  let a1 = new Animal() //Animal
  ```

##### class的构造器使用方法

- 给构造函数传值，并且打开控制台仔细观察会发现下面的信息：

  ```js
  function Person (name, age){
    this.name = name
    this.age = age
  }
  const p1 = new Person('王多多' , '18')  
  console.log(p1)
  
  # 上面的信息在控制台打出来的信息如下：
  
  Person {name: "王多多", age: "18"}
          age: "18"
          name: "王多多"
          __proto__:  // 点击打开这个—__proto__里面就会出现constructor
          constructor: ƒ Person(name, age)  //可以发现这个构造器里面是之前写的构造函数
          __proto__: Object  
            constructor(){}
  
  # 通过上面的信息可以得出两个结论:
  1. 构造函数里面有个构造器
  2. 构造器里面是之前写的构造函数
  ```

- 那么使用class呢？

  ```js
  class Animal {
    constructor(name. age){  //通过上面构造函数里面打印出来的信息可以知道这个里面保存的是构造函数
      this.name = name  		//所以可以使用这个显式的给构造器传值 
      this.age = age   
    }
  }
  let a1 = new Animal('大黄', 13)  
  console.log(a1) 
  // 会发现在信息里面没有constructor的信息，但是在下划线原型里面有
  // 也就是说只要是 类，里面必然存在构造器， 只是构造器没有被人为指定的时候隐藏了
  
  # 需要注意的是:每当 new 的时候，都会优先执行构造器里面的构造函数
  ```

  

##### 实例属性和静态属性

- 经过上面的分析可以知道：每次 new 的时候，都会优先执行构造器里面的构造函数，所以通过给`class `显式的指定一个构造器，会把隐藏的构造器覆盖。

- new 一个实例，传值给构造器，这个构造器里面的 this 的属性就叫做实例属性；同样，在构造函数中，this的属性也是实例属性

  ```js
  function Person(name, age){
    this.name = name,
    this.age = age
  }
  const p1 = new Person('王多多' , '18')  
  
  console.log(p1.name)  //通过new出来的实例，访问到的属性，叫做【实例属性】
  console.log(p1.age)
  
  ---------------------------------------华丽的分割线-------------------------------------
  class Animal{
     constructor(name, age){
      this.name = name  //  在构造器里面通过this分配的属性也叫【实例属性】
      this.age = age
   }
  } 
  const a1 = new Animal('大黄', 13)    
  console.log(a1.name)
  console.log(a1.age)
  ```

  

- 通过上面的代码演示已经知道了什么叫做实例属性了，那么什么是静态属性

  ```js
  function Person(name, age){
    this.name = name,
    this.age = age
  }
  Person.info = "这是Person构造函数自己身上的属性"
  const p1 = new Person('王多多' , '18')  
  console.log(p1.info) //通过p来访问info属性会发现是undefined
  console.log(Person.info) //只能通过构造函数来访问这个属性 这个属性就叫做静态属性
  
  --------------------------------------华丽的分割线-----------------------------------------
  
  class Animal{
   constructor(name, age){ #class下函数的方式
      this.name = name  //  在构造器里面通过this分配的属性也叫【实例属性】
      this.age = age
   }
    static info = "eeee"  //在class里面通过 static 这个来写静态属性
  } 
  const a1 = new Animal('大黄', 13)  
  console.log(a1.info)  //undefined 实例点出来的属性是不能访问到的
  console.log(Animal.info)  //info是Animal的静态属性 只能通过构造函数本身访问
  
  # 总结：静态属性就是构造函数自己身上的属性，只能通过构造函数来访问
  ```

  

##### 实例方法和静态方法

- 构造函数-创建实例方法

  ```js
  分析：给构造函数创建一个方法应该创建在哪儿？
  1. 创建在构造函数里面 和 this属性放在一起，只要实例一创建，方法也会被创建
  2. 创建在原型对象上，实例需要使用的时候再调用
  # 答案是：创建在原型对象上。因为如果创建在构造函数里面，那么只要实例一创建就会有，那么不管是这个实例需要不需要，这个方法都在那里占据着内存，假如1000个实例同时被创建，有999个都不需要这个方法，那么这个999个方法就是多余的，占据着多余的内存
  ```

  ```js
  function Person(name, age){
    this.name = name,
    this.age = age
  }
  Person.info = 'aaaa' 
  
  Person.prototype.say = function(){   //这个say是挂载到这个原型对象上的
    console.log('这是一个Person的实例方法')
  }
   
  const p1 = new Person('王多多' , '18')  
  console.log(p1) 
  # 打印出的信息：
  //直接将这个实例对象p1打印出来，将对象点击打开会出现下面的信息：
  Person {name: "王多多", age: "18"}
  age: "18"
  name: "王多多"
  __proto__:
       say: ƒ ()   #  说明这个方法确实是挂载到原型对象上的
       constructor: ƒ Person(name, age)
       __proto__: Object
  ```

- Class 创建实例方法 - 既然构造函数能够创建实例方法，那么class这种也是可以创建实例方法的

  ```js
  class Animal{
     constructor(name, age){
      this.name = name
      this.age = age
     }
   
     static info = "eeee"
    
    //这是动物的实例方法 => 今后会经常用到实例方法
     jiao (){  //  
      console.log('动物的实例方法')
     }
   }
  
  const a1 = new Animal('大黄', 13)  
  a1.jiao()  //实例方法
  console.log(a1)
  # 打印出来的信息：
  Animal {name: "大黄", age: 13}
  age: 13
  name: "大黄"
  __proto__:
        constructor: ƒ Animal(name, age)
        jiao: ƒ jiao()  =>答应出来的信息里面确实是在原型对象上出现了这个jiao方法
        __proto__: Object
        
  # 总结：
  # 1. class里面写实例方法就是写在和  constructor  static 平级的下面 
  # 2. 通过这种方法定义的方法 是和 构造函数原型上定义的方法是一样的，也是在原型上     
  ```

- 构造函数的静态方法

  ```js
  function Person(name, age){
    this.name = name,
    this.age = age
  }
  Person.info = 'aaaa' 
  Person.prototype.say = function(){  //这个say是挂载到这个原型对象上的
    console.log('这是一个Person的实例方法')
  }
  # 静态方法
  Person.show = function(){
    console.log('这是Person的静态show方法')
  }
  
  const p1 = new Person('王多多' , '18')  
  p1.say()
  // p1.show() //定义的静态方法 再 通过实例方法来访问就会报错
  // 06-静态方法.js:30 Uncaught TypeError: p1.show is not a function 
  Person.show()  //只能通过这个方法来访问实例对象的方法 这是一个Person的实例方法
  
  console.log(p1) 
  // Person {name: "王多多", age: "18"}
  // age: "18"
  // name: "王多多"
  // __proto__:
        // say: ƒ ()
        // constructor: ƒ Person(name, age)
            // info: "aaaa"
               show: ƒ () #这是通过构造函数来定义的方法 都挂载给了构造函数 并不在原型对象上
            // arguments: (...)
            // caller: (...)
            // length: 2
            // name: "Person"
            // prototype: {say: ƒ, constructor: ƒ}
            // __proto__: ƒ ()
            // [[FunctionLocation]]: 06-静态方法.js:12
            // [[Scopes]]: Scopes[3]
         // __proto__: Object
  ```

- class的静态方法

  ```js
  class Animal{
     constructor(name, age){
      this.name = name
      this.age = age
     }
     static info = "eeee"  //静态属性今后用的不多
  
     jiao (){  
      console.log('动物的实例方法')
     }
  
    #不管是静态方法还是静态属性 只要前面写上 static 那么就可以变成静态
     static show(){   //这种静态方法今后用的不多
      console.log('这是Animal的静态 show 方法')
    }
   }
  
  const a1 = new Animal('大黄', 13)  
  
  a1.jiao()
  Animal.show()   //静态方法
  console.log(a1)
  
  // Animal {name: "大黄", age: 13}
  // age: 13
  // name: "大黄"
  // __proto__:
  //       constructor: ƒ Animal(name, age)
  //           info: "eeee"
  //           arguments: (...)
  //           caller: (...)
  //           length: 2
  //           name: "Animal"
  //           prototype: {constructor: ƒ, jiao: ƒ}
               show: ƒ show()  #静态方法 并不在原型对象上 而是在构造器里面的构造函数里面
  //           __proto__: ƒ ()
  //           [[FunctionLocation]]: 06-静态方法.js:54
  //           [[Scopes]]: Scopes[4]
  //       jiao: ƒ jiao()
  //       __proto__: Object
  ```

- 需要注意的是`class`{ }内部是只能写`constructor` ,`静态属性`/`静态方法`  , `实例属性/实例方法` 其他是不能写的

- class内部还是用原来的配方实现的，就是普通的构造函数，所以我们把class关键字，称做语法糖

##### class基本使用方法总结：

- 每个class的内部都有一个构造器`constructor`
- 在new这个class的时候是第一时间去执行构造器里面的内容
- 通过new之后传递的参数，都通过构造器的形参列表进行接收，内部也是使用this来进行分配的

##### class实现继承的方法

- 属性继承

```js
//定义一个美国人
class American {
 constructor(name, age){
    this.name = name
    this.age = age
  }
}
const a1 = new American('Jack', 20)
console.log(a1)


// 定义一个中国人
class Chinese{
  constructor(name, age){
    this.name = name
    this.age = age
  }
}
const c1 = new Chinese('张三', 111)
console.log(c1)

# 上面是定义了两个国家的人 ，如果要定义全球的人 是不是要定义100个类？
```

```js
观察上面两个类发现，其中的构造器里面的内容是一样，是不是有个方法可以将构造器的内容写到一起，然后别的国家直接使用这个方法就好了？
# class里面定义了 继承 的概念，可以将一些相同的内容抽离出来，写到一个共同的方法里面，然后其他类引用就好了
改造上面的代码？

//这是父类  大家可以直接把父类 理解成原型对象
class Person {  //将几个类里面一样的内容抽离出来一个单独的内容
  constructor(name, age){
    this.name = name
    this.age = age
  }
}

// 这是子类 美国人
// 在class类中，可以使用extends 关键字，实现子类继承父类
// 语法：class  子类 extends（继承） 父类 
class American extends Person{  # 这里要想使用上面的方法，就是在后面加上 继承关键字 和 要继承的名字
  
}
const a1 = new American('Jack', 20)
console.log(a1)


// 这是子类中国人
class Chinese extends Person {
  
}
const c1 = new Chinese('张三', 111)
console.log(c1)

# 通过在类 后面加上 extends 关键字 和 父类的名字 实现继承， 这样相同的部分就不用再重复写了
```

- 方法继承： 和属性继承一样
##### 构造器中的super方法

```js
class Person {
  constructor(name, age){
    this.name = name
    this.age = age
  }
  sayHello(){
    console.log('大家好')
  }
}

class American extends Person{
  constructor(){  //在子类使用extends关键字继承父类的时候，如果在这里写一个构造器，报错显示需要一个super()函数，那么这个sper函数是什么？
    
    super()
  }
}
const a1 = new American('Jack', 20) 
console.log(a1)
```

- 什么是super?
  - **语法层面的规定**：如果一个子类通过`extends`关键字继承父类的属性和方法的时候，必须在构造器里面优先调用`super()`方法

- super()是个什么东西
  - 通过super()的写法，猜测super是个函数，经过测试发现super确实是个函数
  - 不过不仅只是个函数，还是**父类的构造器**的一个指引

- 为什么调用了super()之后.a1实例的name和age都变成undefined构造器中的一个引用？
  - 之前说过，只要`new`一个类，那么就必然优先去执行这个类的构造器，而这个构造器里面没有传入参数列表进行接收，那么就是`name=undefined`,age=undefined, 这两个又传`super`，supe函数是父类的构造器，super函数里面也没有传入参数列表进行接收，自然也是两个undefiend.
  - 所以j解决这个问题的办法是给constructor 和super 都手动传入参数列表进行接收

- 为什么没有给子类加constructor这些东西之前就不报错，加了之后反而还报错？
  - 还是之前说过的，只要`new`一个类，会优先去执行这个类的构造器
  - 之前还说过，每个类都有一个隐藏的`constructor`，但是一旦手动添加了`constructor`，那么这个`constructor`会自动覆盖隐藏的`constructor`
  - 手动添加了`constructor`,参数列表不传，父类的构造器`super()`函数不传，相当于这是放了一个空箱子在这里占位置，但是里面没有零件，自然启动之后就会出现各种报错。
  - 所以只要是子类继承父类，手动添加`constructor`,一定要添加super()函数，并且一定要记得传参接收

- 什么情况会使用`super()`?
  - 只要使用extends关键字实现继承，一定要记得在子类构造器里面加上`super()`，并且传递参数

##### 为子类挂载独有的属性

- 并不是所有的子类都是一样的，比如美国人就没有中国人的身份证，那么这个时候想要给中国人一个属性，怎么添加？

  ```js
  class Person { 
    constructor(name, age){   //所有子类都共享的东西适合放在父类  
      this.name = name
      this.age = age 
    }
    sayHello(){
      console.log('大家好')
    }
  }
  class Chinese extends Person {
    constructor(name,age,IDNumber){ # IDNumber是中国人独有的，不能放在父类，只能放在子类自己的构造器里面
      super(name,age,IDNumber)  
      this.IDNumber = IDNumber  # 在子类中，this 只能放到super之后使用
    }
  }
  const c1 = new Chinese('张三', 111 ,513701996)
  console.log(c1)
  ```

- 总结：

  - 需要共享的属性都适合放在父类的构造器，需要共享的函数放在父类的函数里面
  - 不需要共享的就放在自己的类的构造器里面，传值给构造器进行接收就可以了
  - **特别需要注意的是：通过this分配属性的时候，这个this不能放在super函数前面，不然会报错**
  - 也就说，constructor里面执行的第一行代码必须是super函数

##### 

#### 6.创建组件的方式二（class）

##### 最基本的组件结构

```jsx
class 组件名称 extends React.Component { 
  render(){
    return <div>这是class创建的组件</div>
  }
}

#总结：
1.如果要使用 class 定义的组件，必须让自己的组件继承自父类的组件
2.React.Component是一个类 当我们自己的类继承了React.Component的类，那么自己的类就有父类的一些特				征，因为子类继承父类，所以父类上的东西子类上也有
3.在组件内部，必须有render函数，render函数的作用是渲染当前组件所对应的虚拟DOM元素
4.render函数中，必须返回合法的JSX虚拟DOM结构 
```

##### 基本骨架

```jsx
class Movie extends React.Component {
  render(){
   return <div>这是class创建的组件 - </div>
  }
}

ReactDOM.render(
  <div> #根容器 
     <Movie></Movie> 将创建的组纪以标签形式放到这里  
  </div>,
  document.getElementById('app')
)

```

##### 为class创建的组件传递props参数

```jsx
class Movie extends React.Component{
  render(){  //实例方法
    // 在class 关键字创建的组件中，如果想使用外界传递过来的props参数，不需要接收，
    // 直接通过this.props.***接收即可
    return <div>
      {/* 注意：在class组件内部，this表示当前组件的实例对象 */}
      这是Movie组件 - {this.props.name} - {this.props.age} - {this.props.gender}
    </div>
  }
}

const user = {
  name: 'zs',
  age: 22,
  gender: '男'
}

ReactDOM.render(
  <div>
      {/* 这里的movie标签，其实就是movie类的一个实例对象 */}
      <Movie {...user}></Movie>
  </div>,
  document.getElementById('app')
)
```

##### class组件中的props是只读的

- 之前使用function创建的组件里面的props是`read-only`,但是class里面的组件是没有这个read-only这个标签的，那么是不是说明使用class关键字创建的组件的props是可读可写的？？

  ```jsx
  class Movie extends React.Component{
    render(){  
      this.props.name = '李四' 
      
  # 加完这句话之后句报错：
  # Uncaught TypeError: Cannot assign(分配) to read only property 'name' of object '#<Object>'
  #意思是props属性是只读属性，不能更改写入
  
      return <div>
        这是Movie组件 - {this.props.name} - {this.props.age} - {this.props.gender}
      </div>
    }
  }
  
  #结论：
  不管是function还是class创建的组件props，都是read only
  ```

  

#### 7.两种创建组件方式的对比

```jsx
function Hello (props){
  return <div>这是function创建的组件 - {props.name} - {props.age} - {props.gender}</div>
}

class Movie ectends React.Component{
  render(){
    return <div>这是class创建的组件 - {props.name} - {props.age} - {props.gender} </div>
  }
}
```

##### 相同点

- Function 和 class 创建的组件都能以 **标签的形式** 被丢到页面上显示
- Funciton 和 calss 创建的组件都能直接给传参，传过来的参数也能被访问
  - Function 直接是使用 `props` 接收
  - Class 是使用 `this.props`接收

> 如果两个创建组件的特征一样，为啥还要设计两个创建组件的方式？

既然创建两个，肯定有区别，那么区别是哪些？



##### 不同点

==概念问题：使用class关键字创建的组件，有自己的私有数据和生命周期函数；但是使用function创建的组件，只有props，没有自己的私有数据和生命周期函数==

- 对比vue中，每个组件都有自己的私有数据（data方法），有自己的生命周期函数，像before / creact / created / mounted ， 在React中使用`class`创建的组件也有自己的私有数据和生命周期函数，但是如果是使用function创建的组件是没有这些的



#### 8.class创建的组件的私有数据

##### this.state只能写在class组件里面

```js
class Movie extends React.Component{
  constructor(){
    super() 
    this.state = {   
      msg: '大家好，我是class创建的Movie组件'
    }  
  }

  render(){   
    return <div>
      这是Movie组件---{this.props.name}---{this.props.age}--{this.props.gender}
      <h3>{this.state.msg}</h3>  # 只能放到class里面
    </div>
  }
}

const user = {name: 'zs',age: 22,gender: '男'}
 
ReactDOM.render(
  <div>
       <Movie {...user}></Movie>
       <h3>{this.state.msg}</h3>  # 在这里调用这个会报错： index.js:57 Uncaught TypeError: Cannot read property 'state' of undefined
  </div>,
  document.getElementById('app')
)
```

##### this.state数据是可读可写的

```jsx
class Movie extends React.Component{
  constructor(){
    super()  
    this.state = {  //这个this.state = {}就约等于 Vue中的 data(){ return {}}
      msg: '大家好，我是class创建的Movie组件'
    }  

    // 这个state是只读只写的吗？ =>可读可写的
    // 因为这个this.state是react里面的东西 相当于vue中的data 
    // 在vue中的data中那些数据是可读可写的
    // 既然相当于，那么this.state中的数据也是可读可写的
  }

  render(){   
    // this.state.msg = 'msg的值被我修改了' 事实证明，state是可读可写的
    return <div>
      这是Movie组件---{this.props.name}---{this.props.age}--{this.props.gender}
      <h3>{this.state.msg}</h3>  //只能放到class里面
    </div>
  }
}

const user = {name: 'zs',age: 22,gender: '男'}

ReactDOM.render(
  <div>
       <Movie {...user}></Movie>
  </div>,
  document.getElementById('app')
)
```

##### 两种状态组件

- 因为构造函数没有`state`这个私有的数据，所以构造函数创建出来的组件，叫做"无状态组件"

- 因为class 里面有`state`这个私有的数据，所以class创建的组件叫做"有状态组件"

- 有状态组件和无状态组件之间的本质区别是：有无state属性 和 有无生命周期函数

- 怎么区分使用哪种组件？

  - 如果一个组件需要自己的私有数据，则推荐使用：class创建的有状态组件

  - 如果一个组件不需要私有的数据，则推荐使用：无状态组件

  - React官方说：无状态组件，由于没有自己的state和生命周期函数，所以运行效率会比有状态组件稍微高一些

    

##### props和state/data中的区别

##### props和state/data中的区别

- 数据来源

  - props中的数据都是外界传递过来的；

  - state/data中的数据，都是组件私有的；（通过AJax获取回来的数据，一般都是私有数据）

    

- 数据特性

  - props中的数据都是只读的，不能重新赋值；
  - state/data中的数据都是可读可写的

#### 9.将index.js的文件中的组件抽离出去

```jsx
import React from 'react'
import ReactDOM from 'react-dom'

function CmtItem(props){  #function定义的无状态组件
  return  <div >
      <h1>评论人： {props.user}</h1>
      <p>评论内容： {props.content}</p>
  </div>
}

class Cmtlist extends React.Component{ #class定义的有状态组件
  constructor(){
    super()
    this.state = { #有this.state表示有状态
      CommentList: [ //评论列表数据
        {id: 1, user: '张三', content: '哈哈，沙发'},
        {id: 2, user: '李四', content: '哈哈，沙发'},
        {id: 3, user: '王五', content: '哈哈，沙发'},
        {id: 4, user: '赵六', content: '哈哈，沙发'},
        {id: 5, user: '田七', content: '哈哈，沙发'},
      ]
    }
  }
  render(){
    return  <div>
    <h1>这是评论列表内部</h1>
    {this.state.CommentList.map(item => <CmtItem {...item} key={item.id}></CmtItem> )}
  </div>
  }
}

ReactDOM.render(
  <div>
     <Cmtlist></Cmtlist>
        
  </div>,
  document.getElementById('app')
)
```

##### 在src文件夹下建立单独的组件文件夹

- 将上面的`function`组件 和 `class`组件抽离为两个单独的组件
  - 在`src` 文件夹下面新建`components`文件夹。这个文件夹是专门用来放各种单独的文件夹的
  - 新建`CmtList.js`文件
  - 新建`CmtItem.js`文件

- 开始分离组件-CmtItem.js文件内容 - 

  - 将组件内容复制到这个文件夹中,因为组件有单独的作用域，所以要使用export default导出这个模块

  ```js
  export default function CmtItem(props){  # 第一步：将组件内容复制到这个文件夹中
    return  <div >
        <h1>评论人： {props.user}</h1>
        <p>评论内容： {props.content}</p>
    </div>
  }
  ```

  - 因为单独组件中也要使用react,所以也要导入react

  ```js
  import React from 'react' #第二步：导入这个包
  ```

  - 这个单独的组件就分离出去了



- 开始分离组件-CmtList.js文件内容

  - 将组件内容复制到这个文件夹中,使用模块导出语法将这个模块导出

    ```jsx 
    export default class Cmtlist extends React.Component{
      constructor(){
        super()
        this.state = {
          CommentList: [ //评论列表数据
            {id: 1, user: '张三', content: '哈哈，沙发'},
            {id: 2, user: '李四', content: '哈哈，沙发'},
            {id: 3, user: '王五', content: '哈哈，沙发'},
            {id: 4, user: '赵六', content: '哈哈，沙发'},
            {id: 5, user: '田七', content: '哈哈，沙发'},
          ]
        }
      }
      render(){
        return  <div>
        <h1>这是评论列表内部</h1>
       {this.state.CommentList.map(item => <CmtItem {...item} key={item.id}></CmtItem> )}
      </div>
      }
    }
    ```

  - 第二步是导入react包

    ```js
    import React from 'react'
    ```

  - 因为这个组件是引入了评论的组件，所以要将评论的组件导入到这个组件

    ```js
    import CmtItem from '@/components/CmtItem'
    ```

##### 导入文件的路径 - @  

- 如果要抽离组件了，之前是在A文件中，挪动到B文件，从B文件挪到C文件，然后这个路径就会跟着挪来挪去

- 如果是使用`./`这种方式来写路径，那么需要一直改路径

- 之前在`webpack.config.js`中设置过的一个路径设置：

```js
alias: {
      '@': path.join(__dirname, './src')
    }
```

- 在路径中以`@`符号来设置路径，这个@已经被处理成一个绝对路径了。因为是从C盘或者D盘的盘符来算起。然后就可以在组件的任何文件里面使用`'@/components/+文件名`，因为是个绝对路径。

#### 10.在jsx中使用行内样式

- 行内样式的语法

```jsx
 render(){
    return  <div> 
    <h1 style="color:red;">这是评论列表内部</h1>  #在使用style="color:red;"这个行内样式的时候会报错
    {this.state.CommentList.map(item => <CmtItem {...item} key={item.id}></CmtItem> )}
  </div>
  }

# 报错信息如下：
未捕获    不变量的    冲突 
Uncaught Invariant Violation: The `style` prop expects a mapping from style properties to values, not a string. For example, style={{marginRight: spacing + 'em'}} when using JSX.

# 注意：
在JSX中，如果想写行内样式，不能为 style 设置字符串的值
应该这样写： style={{ color: 'red' }}

```

- 样式属性的写法注意事项

  - 类似`font-size`这样有连字符的属性，那么就是将连字符去掉，然后将第二个单词首字母大写

    ```js
    render(){
     return  <div> 
       <h1 style="color:red; font-size: '25px'">这是评论列表内部</h1>  #出现报错信息
       {this.state.CommentList.map(item => <CmtItem {...item} key={item.id}>       </CmtItem> )}
             </div>
    }
    
    # 报错信息： 
    Warning: Unsupported style property font-size. Did you mean fontSize?
    意思是有连字符的属性最少第二个单词首字母大写
    ```

    

  - 如果写行类样式的时候不加双引号，那么就会报错

  - 写属性的时候，如果属性的值是带有字母的，那么就必须给属性值加单引号，如果属性值是纯数字的，那么就不必加单引号

    ```js
    render(){
     return  <div> 
       <h1 style="color:red,zIndex:3,textAlign:'center'">这是评论列表内部</h1>  #出现报错信息
       {this.state.CommentList.map(item => <CmtItem {...item} key={item.id}>       </CmtItem> )}
             </div>
    }
    
    # 报错信息：
    Uncaught ReferenceError: red is not defined
    总结：行内样式中，如果是数值类型的样式，则可以不用引号包裹，如果是字符串类型的样式值，必须使用引号包裹
    ```
#### 11.分离行内样式

- 第一种是自己将行内样式写在标签里面

  ```js
  export default function CmtItem(props){
    return  <div style={// const itemStyle = {border: '1px dashed #ccc',margin: '10px',padding: '10px',boxShadow: '0 0 10px #ccc'}}>
        <h1 style={{fontSize: '14px'}}>评论人： {props.user}</h1>
        <p style={{fontSize: '12px'}}>评论内容： {props.content}</p>
    </div>
  }
  
  # 这个将行内样式写在标签里面，导致每行标签的特别大
  ```

- 第二种是将每个行内样式都抽出来一个单独的变量，然后将变量放在jsx表达式里面

  ```js
  const itemStyle = {border: '1px dashed #ccc',margin: '10px',padding: '10px',boxShadow: '0 0 10px #ccc'}
  const userStyle = {fontSize: '14px'}
  const contentStyle = {fontSize: '12px'}
  
  
  export default function CmtItem(props){
    return  <div style={itemStyle}>
        <h1 style={userStyle}>评论人： {props.user}</h1>
        <p style={contentStyle}>评论内容： {props.content}</p>
    </div>
  }
  ```

  

- 第三种是将每个行内样式批处理，放在一个对象里面，然后使用点的方式将对象的每个数据点出来

  ```js
  const styles = {
      item: {border: '1px dashed #ccc',margin: '10px',padding: '10px',boxShadow: '0 0 10px    #ccc'},
      user: {fontSize: '14px'},
      content: {fontSize: '12px'}
  }
  
  export default function CmtItem(props){
    return  <div style={styles.item}>
        <h1 style={styles.user}>评论人： {props.user}</h1>
        <p style={styles.content}>评论内容： {props.content}</p>
    </div>
  }
  ```

  

- 第四种是抽离为单独的模块文件，建立一个名字为`style.js`文件

  ```js
  export default {
    item: {border: '1px dashed #ccc',margin: '10px',padding: '10px',boxShadow: '0 0 10px #ccc'},
    user: {fontSize: '14px'},
    content: {fontSize: '12px'}
  }
  ```

- 第五种抽离为单独的`css`组件=> 在`components文件夹下，新建一个文件`cmtlist.css`,然后在里面写入样式，最后将这个文件导入到需要这个样式的组件文件中。

  

##### webpack配置解析.css文件

- 安装解析.css文件的安装包

  ```js
   npm i style-loader css-loader -D
  ```

- 打开`webpack.config.js`文件，在webpack官网找到`style-loader`的配置文件，然后将配置文件复制到这个文件里面

  ```js
  {
    test: /\.css$/,
    use: [{ loader: 'style-loader' }, { loader: 'css-loader' }],
   }
   resolve: {
      extensions: ['.js','.jsx','.json','.vue'],  
  ```

- 因为新配置过的文件要重新启动才生效，所以这里需要重启服务才行

- webpack解析.css文件的过程：

  - 第一步：webpack在执行到`import cssobj from '@/css/cmtlist'   `这句代码的时候，会发现这句代码执行不了
  - 第二步：在发现自己解析不了这句代码的时候，那么就会去自己的配置文件`webpack.config.js`里面去找，然后就会找到我们配置的解析css后缀名的那句代码
  - 第三步：按照从右往左的顺序，先使用`css-loader`来执行这个文件，然后`css-loader`将处理结果传递给`style-loader`， 等到`style-loader`将结果处理好之后，发现自己旁边没有处理器了，就会把结果交给webpack，webpack进行打包处理。

  

##### webpack启用css-modules

```js
import cssobj from '@/css/cmtTitle.css'
console.log(cssobj) //{}

分析：这里导入的css样式表 ，导出的是一个空对象，所以是没有作用域的，导致只要引入这个文件，这个文件的样式就会作用在文件上面
要解决的问题: 将css样式表的作用域变成类似模板作用域一样的东西
解决的办法：官方已经给了解决办法-启动css-modules
```

- 第一步：修改`webpack.config.js`这个配置文件，为css-loader添加参数`?modules`

  ```js
   // 可以在css-loader之后，通过？追加参数。其中。有个固定的参数，叫做modules,表示为 普通的css
   use: [{ loader: 'style-loader' }, { loader: 'css-loader?modules' }], 
  ```

- 第二步：在需要的组件中，`import`导入样式，并接收模块化的css样式对象

  ```js
  import cssobj from '../css/CmtList.css'
  ```

- 第三步：在需要的HTML的标签上，通过`对象.属性`形式使用className指定模块化的样式

  ```jsx
  <h1 className={cssobj.title}>评论列表组件</h1>
  ```

#### 12.webpack设置自定义类名

- 因为自动生成的类名是在太个性了，就像一堆乱码，我们都不知道那是啥，于是为我们提供了另外一对参数，可以自定义类名生成类名。

- 自定义类名设置方法：

  - 使用`localIdentName`自定义生成的类名格式，可选的参数为：

  - 【path】表示样式表`相对于项目根目录`所在路径

  - 【name】表示样式表文件名称

  - 【local】表示样式的类名定义名称

  - 【hash:length】表示32位的hash值

  - 放入webpack.config.js的代码：

    ```js
          {
            // For CSS modules
            test: /\.css$/,
            use: [
              "style-loader",
              {
                loader: "css-loader",
                options: {
                  modules: true,
                  modules: {
                    localIdentName: "[path][name]-[local]-[hash:base64:5]"
                  }
                }
              }
            ]
          },
    ```

    经过上面设置后打印出来的对象为：

    ```js
    Object
    cmtTitle: "src-css-cmtlist-cmtTitle-2niaj"
    test: "src-css-cmtlist-test-3KlWr"
    title: "src-css-cmtlist-title-12gry"
    ```

    

#### 13.使用:global和:local

- `:local`包裹 的类名，是被模块化的类名，只能通过`className={cssobj.类名}`来使用，同时，`：local`默认可以不写，这样，默认在样式表中定义的类名，都是被模块化的类名
- `:global`包裹的类名，是全局生效的，不会被`css-modules`控制，定义的类名是什么，就是使用定义的类名`className="类名"`

#### 15.配置bootstrap和解析scss文件

##### 安装`bootstrap@3.3.7` 

- 导入文件里面

```js
npm install bootstrap@3.3.7 -s

import bootcss from 'bootstrap/css/dist/bootstrap.css'

<button className="btn btn-primary">按钮</button>
# 使用上面bootstrap这种类名会报错：
 会显示无法解析.svg|eot|ttf|woff|woff2这类文件
```

- 解决无法解析文件后缀名的问题：

  - 安装`url-loader`和`file-loader`

    ```js
    npm install url-loader file-loader -s
    ```

  - 然后在`webpack.config.js`文件中加入下面的代码

  ```js
  {
    test: /\.(png|jpg|gif|svg|eot|ttf|woff|woff2)$/,
    loader: "url-loader",
    options: {
       limit: 10000,
          },
   },
  ```

  

- 解决完上面的问题之后会发现没有效果，然后将导入的`bootcss`打印出来会发现是个对象,需要将属性点出来使用

  ```js
  <button className={[bootcss.btn , bootcss['btn-primary']].join(' ')}>按钮</button> 
  # 使用这种方式就不能直接使用bootstarp里面的类名了 还是希望能直接使用bootstrap里面的类名
  ```

  

- 怎么样才能直接使用bootstrap里面的类名？

  通过观察发现，打印出来`bootcss`的对象发现，里面的类名都被模块打包了，也就说之前是将`.css` 后缀名设置为通过模块打包。

  现在我们导入的`bootstrap.css`的文件是不需要通过模块打包的，怎么样将这个文件隔离出去？

  解决办法是将css样式表里面的文件都改为.scss结尾的文件，然后`bootstrap.css`这类似的文件还是用.css文件后缀名，但是这样就需要重新设置能够解析scss文件的loader.

##### 安装解析scss文件的loader

- 找到`webpack`设置scss文件的地方（英文版）：

```js
    # 安装配置文件
    npm install sass-loader node-sass --save-dev

```

- 配置代码：

  ```js
  {
          test: /\.s[ac]ss$/i,
          use: [
            // Creates `style` nodes from JS strings
            "style-loader",
            // Translates CSS into CommonJS
            {
              loader: "css-loader",
              options: {
                modules: {
                  localIdentName: "[path][name]__[local]--[hash:base64:5]",
                },
              },
            },
            // Compiles Sass to CSS
            "sass-loader",
          ],
        },
  ```

  

##### 设置这样代码的原因

- 之前解析.css后缀名的样式表是可能里面要写scss文件，所以设置为了如下代码：

  ```js
    {
          // For CSS modules
          test: /\.css$/,
          use: [
            "style-loader",
            {
              loader: "css-loader",
              options: {
                modules: true, #选择模块化
                modules: {
                  localIdentName: "[path][name]-[local]-[hash:base64:5]"
                }
              }
            }
          ]
        },
  ```

  - 但是现在.css文件只是引入进来的下载好的文件包，不需要使用scss解析，也不需要模块化，所以需要将模块化的设置删掉，只留下包名就可以了，也就是代码设置改为如下：

  ```js
   {
          test: /\.css$/,
          use: ["style-loader", "css-loader"], #css-loader这里不需要模块化，需要全局引用
        },
  ```

##### 配置解析.scss文件最终版

```js
 {
        test: /\.s[ac]ss$/i,
        use: [
          // Creates `style` nodes from JS strings
          "style-loader",
          // Translates CSS into CommonJS
          {
            loader: "css-loader",
            options: { #设置css模块化
              modules: {
                localIdentName: "[path][name]__[local]--[hash:base64:5]",
              },
            },
          },
          // Compiles Sass to CSS
          "sass-loader",
        ],
  },
```

这样子设置好了之后就可以正常解析`bootstrap.css`文件和`.scss`文件

##### 设置好之后的使用方法

```js
# 将之前后缀名为.css文件都重命名为.scss后缀名的文件再重新引入进来
import cssobj from '@/scss/cmtlist.scss'
 
# 由于bootstrap的包文件不需要模块化 而且也并没有导入对象 所以不需要import XX from 这种导出文件的方式
import 'bootstrap/dist/css/bootstrap.css'

export default class Cmtlist extends React.Component{
  constructor(){
    super()
    this.state = {
      CommentList: [  
        {id: 1, user: '张三', content: '哈哈，沙发'},
        {id: 2, user: '李四', content: '哈哈，沙发'},
        {id: 3, user: '王五', content: '哈哈，沙发'},
        {id: 4, user: '赵六', content: '哈哈，沙发'},
        {id: 5, user: '田七', content: '哈哈，沙发'},
      ]
    }
  }
  render(){
    return  <div>
      
---------------直接写bootstrap的类名------------------------------------------------------
     <button className="btn btn-primary">按钮</button>
---------------直接写bootstrap的类名------------------------------------------------------
    
    <h1 className={[ cssobj.title , "test" ].join(' ')}>这是评论列表内部</h1>
    {this.state.CommentList.map(item => <CmtItem {...item} key={item.id}></CmtItem> )}
  </div>
  }
}
```

- 到这里css文件解析就完成了
    




#### 1.react绑定机制

- 传统的绑定方式为：

  ```js
  <button onclick="">按钮</button>
  # 报错信息：
  react-dom.development.js:558 Warning: Invalid event handler property `onclick`. Did you mean `onClick`?
  分析：
  报错信息的意思是onclick 应该为 onClick 
  这样看来，react的事件绑定机制应该是有一套自己的事件处理函数的机制，
  事件名应该是小驼峰命名
  ```

- 将onclick改为onClick 

  ```js
  <button onClick="">按钮</button>
  
  #报错信息：
  Warning: Expected `onClick` listener to be a function, instead got a value of `string` type. 期望的onclick监听应该是个函数，而不是个字符串
  ```

- 将onclick改为一个函数

  ```js
  <button onClick={function(){console.log('ok')}}>按钮</button>
  ```

  

##### 事件绑定语法

- 经过上面的分析可以看出来，react的事件处理函数的格式必须要符合两点：

  - 必须为驼峰式命名 ，类似`onClick` `onMouseOver`

  - 表达式必须为一个函数 ，类似`onClick={function(){}}`

    

- 用的最多的事件绑定形式为：

  ```jsx
  <button onClick={ () => this.show('传参') }>按钮</button>
  //事件处理函数，需要定义为一个箭头函数，然后赋值给 函数名称
   show = (arg1) => {
      console.log('show方法'+ arg1)
    }
  
  show等于一个箭头函数，本来箭头函数就是一个匿名函数，我们是想在点击的时候触发onclick函数，能调用吗
  (arg1) => {
      console.log('show方法'+ arg1)
    }
  
  本身这个箭头函数是个匿名函数，没有名字，那么我们也调用不了，所以要想将箭头函数抽离出来，就必须给箭头函数起一个名字，这样子箭头函数就变成一个具名函数了
  先定义一个function，再将这个function 的引用赋值给这个 show的名字 ， 那个show 这个成员就指向这个箭头函数了，那么在触发点击事件的时候就能根据这个函数名来触发这个箭头函数了
    
  所以这种方法是最靠谱的：
  1.先定义一个箭头函数，
  2.在箭头函数里面写方法的调用
  3.赋值给一个具体的函数名
  ```

##### 事件传参方式

```js
  <button onClick={() => this.show("🐖", "🏃")}>按钮</button>

   show = (arg1, arg2) => {
     console.log(this.state.msg + arg1 + arg2)
  };
```

##### 修改状态值

```js
  <button onClick={() => this.show("🐖", "🏃")}>按钮</button>

   show = (arg1, arg2) => {
     this.setState({  #注意这里使用this.state.msg =  "123" + arg1 + arg2 是没有效果的 
      msg: "123" + arg1 + arg2
    });
  };
```

##### setState异步执行

```js
show = (arg1, arg2) => {
    this.setState({  
      msg: "123" + arg1 + arg2
    },function(){
      console.log(this.state.msg)
    });
  
console.log(this.state.msg)  =>这里打印出来的是之前的内容 不是最新的数据
# 是因为this.setState是异步执行的，所以会先执行完同步的内容再执行异步的内容，如果是想想拿到最新的数据，使用callback函数异步调用，这样就可以拿到最新的数据
```

#### 2.实现双向绑定文本框的值

默认情况下，在react中，如页面上的表单元素，绑定了state上的状态值，那么，每当state上的状态值变化，必然会自动把最新的状态值，自动同步到页面上   状态流 => 自动更新页面  这个叫做单向数据流 

如果UI界面上，文本框的内容变化了，想要把最新的值，同步到state中去，此时，React没有这种自动同步机制

##### 使用e.target.value同步

1.在react中，需要程序员手动监听文本框的onChange事件，

```js
 <input type="text"  value={this.state.msg} onChange={(e)=> { this.textChanged(e)}}/> 
```



2.在onChange事件中，拿到最新的文本框的值

```js
# 使用e.target.value
textChanged = (e) => {
    // 在 onChange事件中，获取文本框的值有两种方案：
    // 方案一：通过事件参数e来获取
    console.log(e.target.value)
  };
```



3.程序员调用this.setState{()}手动把最新的值同步到state中

```js
 textChanged = (e) => {
    // console.log(this.refs.txt.value)
    // 在react中获取文本框的方式有两种:一种是事件处理函数，一种是使用refs
    const newVal = e.target.value
    this.setState({
      msg: newVal
    })
  };
```



##### 使用refs同步

1.在react中，需要程序员手动监听文本框的onChange事件，

```js
 <input type="text"  value={this.state.msg} onChange={(e)=> { this.textChanged(e)}}/> 
```

2.在onChange事件中，拿到最新的文本框的值

```js
 <input 
        type="text" 
        style={{width: '100%'}} 
        value={this.state.msg} 
        onChange={(e)=> {this.textChanged(e)}} 
        ref = 'txt'/ >   # 使用refs
```

3.程序员调用this.setState{()}手动把最新的值同步到state中

```js
textChanged = (e) => {
    const newVal = this.refs.txt.value  #使用refs实现
    this.setState({  
      msg: newVal
    })
```

##### 组件的生命周期

- 组件的创建阶段： 特点：一辈子执行一次

  ```js
  static Props 初始化属性
  this.state 初始化私有数据 这个会被第一时间执行 因为在构造器里面 只要new了实例，就会执行构造器里面的代码
  
  # mount的意思是挂载，挂载的意思是将虚拟DOM树 放到 页面上 去加载的过程
  
  componentWillMount 组件的虚拟DOM树将要被挂载 但是此时的虚拟DOM树没有被创建出来，没有挂载到页面
  render 渲染 渲染虚拟DOM树 执行完render函数，虚拟DOM树就在内存中创建好了，但是，还没有挂载
  componentDidMount 挂载组件 将内存中的虚拟DOM和数据挂载到页面上 组件显示到页面上 进入运行中状态
  ```

  

- 组件运行阶段：按需，根据props属性或者state状态的改变，有选择的执行0次或者多次

  ```js
  属性是否被修改： 如果修改就会执行 componentWillReceiveProps ，只要执行这个方法，就证明父组件向子组件							传递了新的属性
  
  							执行完上面的函数之后，就会和state状态发生改变一样，执行下面的函数
                
  shouldComponentUpdate  组件是否需要被更新 此时，组件尚未被更新，但是，state和props肯定是最新的 
  componentWillUpdate 组件将要被更新，此时，尚未开始更新，内存中的虚拟DOM树还是旧的
  render  重新渲染更新后的数据或者属性 根据最新的state和props重新渲染一颗内存中的虚拟DOM树，当render调用完毕，内存中的旧DOM树，已经被新的DOM树替换了，此时页面还是旧的
  componentDidupdate 组件升级完毕 此时，页面又被重新渲染了，state和虚拟DOM和页面已经完全保持同步了
  ```

  

- 组件销毁阶段：一辈子只执行一次

  ```js
  componentWillUnmount  组件将要被销毁，此时组件还可以正常使用
  ```

  


  #### 1.react绑定机制

- 传统的绑定方式为：

  ```js
  <button onclick="">按钮</button>
  # 报错信息：
  react-dom.development.js:558 Warning: Invalid event handler property `onclick`. Did you mean `onClick`?
  分析：
  报错信息的意思是onclick 应该为 onClick 
  这样看来，react的事件绑定机制应该是有一套自己的事件处理函数的机制，
  事件名应该是小驼峰命名
  ```

- 将onclick改为onClick 

  ```js
  <button onClick="">按钮</button>
  
  #报错信息：
  Warning: Expected `onClick` listener to be a function, instead got a value of `string` type. 期望的onclick监听应该是个函数，而不是个字符串
  ```

- 将onclick改为一个函数

  ```js
  <button onClick={function(){console.log('ok')}}>按钮</button>
  ```

  

##### 事件绑定语法

- 经过上面的分析可以看出来，react的事件处理函数的格式必须要符合两点：

  - 必须为驼峰式命名 ，类似`onClick` `onMouseOver`

  - 表达式必须为一个函数 ，类似`onClick={function(){}}`

    

- 用的最多的事件绑定形式为：

  ```jsx
  <button onClick={ () => this.show('传参') }>按钮</button>
  //事件处理函数，需要定义为一个箭头函数，然后赋值给 函数名称
   show = (arg1) => {
      console.log('show方法'+ arg1)
    }
  
  show等于一个箭头函数，本来箭头函数就是一个匿名函数，我们是想在点击的时候触发onclick函数，能调用吗
  (arg1) => {
      console.log('show方法'+ arg1)
    }
  
  本身这个箭头函数是个匿名函数，没有名字，那么我们也调用不了，所以要想将箭头函数抽离出来，就必须给箭头函数起一个名字，这样子箭头函数就变成一个具名函数了
  先定义一个function，再将这个function 的引用赋值给这个 show的名字 ， 那个show 这个成员就指向这个箭头函数了，那么在触发点击事件的时候就能根据这个函数名来触发这个箭头函数了
    
  所以这种方法是最靠谱的：
  1.先定义一个箭头函数，
  2.在箭头函数里面写方法的调用
  3.赋值给一个具体的函数名
  ```

##### 事件传参方式

```js
  <button onClick={() => this.show("🐖", "🏃")}>按钮</button>

   show = (arg1, arg2) => {
     console.log(this.state.msg + arg1 + arg2)
  };
```

##### 修改状态值

```js
  <button onClick={() => this.show("🐖", "🏃")}>按钮</button>

   show = (arg1, arg2) => {
     this.setState({  #注意这里使用this.state.msg =  "123" + arg1 + arg2 是没有效果的 
      msg: "123" + arg1 + arg2
    });
  };
```

##### setState异步执行

```js
show = (arg1, arg2) => {
    this.setState({  
      msg: "123" + arg1 + arg2
    },function(){
      console.log(this.state.msg)
    });
  
console.log(this.state.msg)  =>这里打印出来的是之前的内容 不是最新的数据
# 是因为this.setState是异步执行的，所以会先执行完同步的内容再执行异步的内容，如果是想想拿到最新的数据，使用callback函数异步调用，这样就可以拿到最新的数据
```

#### 2.实现双向绑定文本框的值

默认情况下，在react中，如页面上的表单元素，绑定了state上的状态值，那么，每当state上的状态值变化，必然会自动把最新的状态值，自动同步到页面上   状态流 => 自动更新页面  这个叫做单向数据流 

如果UI界面上，文本框的内容变化了，想要把最新的值，同步到state中去，此时，React没有这种自动同步机制

##### 使用e.target.value同步

1.在react中，需要程序员手动监听文本框的onChange事件，

```js
 <input type="text"  value={this.state.msg} onChange={(e)=> { this.textChanged(e)}}/> 
```



2.在onChange事件中，拿到最新的文本框的值

```js
# 使用e.target.value
textChanged = (e) => {
    // 在 onChange事件中，获取文本框的值有两种方案：
    // 方案一：通过事件参数e来获取
    console.log(e.target.value)
  };

```



3.程序员调用this.setState{()}手动把最新的值同步到state中

```js
 textChanged = (e) => {
    // console.log(this.refs.txt.value)
    // 在react中获取文本框的方式有两种:一种是事件处理函数，一种是使用refs
    const newVal = e.target.value
    this.setState({
      msg: newVal
    })
  };

```



##### 使用refs同步

1.在react中，需要程序员手动监听文本框的onChange事件，

```js
 <input type="text"  value={this.state.msg} onChange={(e)=> { this.textChanged(e)}}/> 

```

2.在onChange事件中，拿到最新的文本框的值

```js
 <input 
        type="text" 
        style={{width: '100%'}} 
        value={this.state.msg} 
        onChange={(e)=> {this.textChanged(e)}} 
        ref = 'txt'/ >   # 使用refs

```

3.程序员调用this.setState{()}手动把最新的值同步到state中

```js
textChanged = (e) => {
    const newVal = this.refs.txt.value  #使用refs实现
    this.setState({  
      msg: newVal
    })

```

#### 3.在react绑定this并传参的几种方式

##### 使用Bind函数修改this指向

```jsx
import React from 'react'

export default class BindThis extends React.Component{
  constructor(props){
    super(props)
    this.state = {
      msg: '这是默认的msg'
    }
  } 

  render(){
    return <div>
      <h1>绑定this并传参的几种方式</h1>

{/* bind的作用：
为前面的函数=> 修改函数内部的this指向 , 让函数内部的this=>指向bind参数列表中的第一个参数*/}
    
{/* bind / call / apply的区别：  
    1.call和apply在修改完this指向后会立即调用,但是bind不会
    2.bind只会修改this指向
 */}
<input type="button" value="绑定this并传参的几种方式" onClick={this.changeMsg1.bind(this)}/>
      <hr/>
      <h3>{this.state.msg}</h3>
    </div>
  }

 changeMsg1(){
  //  注意：这里的方式，是一个普通的方法，因此，在触发的时候，这里的this是undefined
  //  console.log(this)  //undefined
  this.setState({
    msg: '绑定this并传参的几种方式'
  })

  console.log(this)  
//绑定完this之后的this信息是这个类 

//   BindThis {props: {…}, context: {…}, refs: {…}, updater: {…}, state: {…}, …}
//     context: {}
//     props: {}
//     refs: {}
//     state: {msg: "绑定this并传参的几种方式"}
//     updater: {isMounted: ƒ, enqueueSetState: ƒ, enqueueReplaceState: ƒ, enqueueForceUpdate: ƒ}
//     _reactInternalFiber: FiberNode {tag: 1, key: null, stateNode: BindThis, elementType: ƒ, type: ƒ, …}
//     _reactInternalInstance: {_processChildContext: ƒ}
//     isMounted: (...)
//     replaceState: (...)
//     __proto__: Component
 }
}

```

##### 使用Bind函数的第二三四五个参数

```js
export default class BindThis extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      msg: "这是默认的msg"
    };
  }

  render() {
    return (
      <div>
        <h1>绑定this并传参的几种方式</h1>
{/* 注意：
bind中的第一个参数，是用来修改this指向的，
第一个参数后面的所有参数，都会当做将来调用 前面函数 时候的参数传递进来 */}
        <input
          type="button"
          value="绑定this并传参的几种方式"
          onClick={this.changeMsg1.bind(this , '这是第二个参数' , '这是第三个参数')}
        />
        <hr />
        <h3>{this.state.msg}</h3>
      </div>
    );
  }

  changeMsg1(arg1,arg2) {
    this.setState({
      msg: "绑定this并传参的第一种方式" + arg1 + arg2
    });
  }
}

```

##### 在类里面绑定this

```js
export default class BindThis extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      msg: "这是默认的msg"
    }

1.绑定this并传参的方式2：在构造函数中绑定this
2.在这里绑定之后去调用参数还是会报错：Uncaught TypeError: Cannot read property 'setState' of undefined
3.注意：当为一个函数，调用bind改变了this指向后，bind函数调用的结果，有一个返回值，这个值，就是被改变this指向后的函数的引用
# 注意：bind不会修改原函数的this指向，如果想要修改，就是将bind函数的修改后的this指向重新赋值给旧的函数，赋值后的this就不指向原函数了
    this.changeMsg2 = this.changeMsg2.bind(this,'💕','❤')   
// 相对bind来说 changeMsg2这个是原函数 当调用完bind函数之后会返回一个新的函数指向 新函数的this变成当前实例 但是原来函数的this没有改变  如果不拿新的东西来接收这个bind函数返回的新的值 那么下面的changeMsg2的this还是等于undefined
// 如果是在事件里面调bind，那么每次使用每次都要调用，但是如果是在全局函数里面调用，那么就只需要调用一次
  }

  render() {
    return (
      <div>
        <h1>绑定this并传参的几种方式</h1>
        <input
          type="button"
          value="绑定this并传参的方式二"
          onClick={this.changeMsg2}
        />
        <hr />
        <h3>{this.state.msg}</h3>
      </div>
    );
  }

  changeMsg2(arg1,arg2) {
    console.log(this)  
    //如果没有一个东西接收bind修改this之后的新函数 原来的函数还是原来的this并没有改变
    //如果想要新的this数据绑定，就必须先接收bind绑定后的新函数的this指向，
    this.setState({
      msg: "绑定this并传参的第二种方式" + arg1 + arg2
    });
  }
}
```

##### 使用箭头函数绑定this

```js
export default class BindThis extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      msg: "这是默认的msg"
    }
  }

  render() {
    return (
      <div>
        <h1>绑定this并传参的几种方式</h1>
        <input
          type="button"
          value="绑定this并传参的方式三"
          onClick={ () => { this.changeMsg3('😁' , '😭') }}
        />


{/* 箭头函数有个特质：箭头函数外部的this   () => { this.changeMsg3('😁' , '😭') } 和
内部的this  this.changeMsg3('😁' , '😭') 要保持一致  会把外部的this 强制绑定到内部的this里面去 
onclick这个函数里面的this是指向 BindThis 这个实例 , 所以箭头函数外部的this就是指向实例 所以内部也会是我们的实例  那既然是实例直接去调用了 那么函数内部的this就是指向我们的调用者 也就是我们的实例

如果这里面不写箭头函数 而是直接 this.changeMsg3('😁' , '😭') 这个函数的调用 react解析到这行的时候 会直接将这个当做函数调用给提交解析掉  所以必须写一个匿名函数 这样子react会到需要调用的时候再解析

*/}

        <hr />
        <h3>{this.state.msg}</h3>
      </div>
    );
  }

  changeMsg3(arg1,arg2) {
    console.log(this)  
 
    this.setState({
      msg: "绑定this并传参的第三种方式" + arg1 + arg2
    });
  }
}
```

##### 实现数据双向绑定

```js
export default class BindThis extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      msg: "这是默认的msg"
    }
  }

  render() {
    return (
      <div>
        <h1>绑定this并传参的几种方式</h1>
        <input
          type="button"
          value="绑定this并传参的方式三"
          onClick={ () => { this.changeMsg3('😁' , '😭') }}
        />
        <hr />
        <h3>{this.state.msg}</h3>

      {/* 在vue中，使用v-model中实现双向数据绑定 
          在react中，使用onChange 实现双向数据绑定
      */}
      <input type="text" style={{width: "100%"}} value={this.state.msg} 
      onChange={ (e) => this.textChanged(e)}/>

      </div>
    );
  }

  textChanged(e){
    // console.log('ok')
    // 如果想要 文本框在触发 onChange 的时候 ，同时把文本框最新的值保存到state中，那么，我们需要手动调用this.setState

    // 货物文本框中最新文本的3种方式：
    // 1.使用 document.getElementByID来拿
    // 2.使用ref 来拿
    // console.log(this.refs.txt.value)
    // 3.使用事件对象的参数e来拿 e.target 就表示触发 这个事件的事件源对象 得到的是一个原生的JSDOM对象
    // console.log(e.target.value) 
    this.setState({
      msg: e.target.value
    })
  }

  changeMsg3(arg1,arg2) {
    console.log(this)  
    this.setState({
      msg: "绑定this并传参的第三种方式" + arg1 + arg2
    });
  }
}
```


