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
