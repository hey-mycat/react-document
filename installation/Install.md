# Installation安装
react是一个灵活的框架，可被用于各种项目。你可以用它创建一个新的应用，你也可以逐渐地将它引入到现有的代码库中，无需再进行重写。

here are a couple of ways to get start `这儿有几种方式供你去开始使用它`
* try react
* create a new app
* Add react to an existing app

## Trying Out React 

如果你只是想玩玩react，你可以使用CodePen。尝试从这个示例开始：[Hello World](https://codepen.io/gaearon/pen/rrpgNB?editors=0010)。你不需要安装任何东西，你可以只改改它的代码，看看它怎么工作。

如果你喜欢用自己的文本编译器，你可以将这段代码[下载](https://raw.githubusercontent.com/reactjs/reactjs.org/master/static/html/single-file-example.html)下来，编辑它，然后在你的浏览器中打开。这是一个很慢很慢的代码改变的过程，所以不要将它用于生产。

如果你想给它用在完整的程序里，这儿有两个特别受欢迎的方式：创建一个[react应用]()，或者将它添加到你的现有的应用程序里。

## Creating a New Application

创建一个react应用是开始构建一个新的react单页应用程序的最佳方式。它帮你搭好了开发环境便于你可以使用最新的javascript功能，提供非常棒的开发者体验，优化你的应用程序的生产。

>您需要在您的机器上`安装node`,版本号要大于6。
``` javascript
npm install -g create-react-app  //全局安装create-react-app
create-react-app my-app //创建名为my-app的项目

cd my-app
npm start //运行
```
>如果您安装了`npm`5.2.0以上的版本，则可以使用npx
```javascript
npx create-react-app my-app
npm start
```
`create-react-app`并没有处理后端逻辑或者数据库；它只创建了一个前端工程`a frontend build pipeline`，所以你可以用它搭配任何后台系统。它使用`babel`，`webpack`之类的打包工具，但工作的时候，并不需要任何配置。

当你准备部署到生产环境时，运行`npm run build`会在你的文件夹里帮你构建一个最合适的app。如果你想进一步了解`create react app`，你可以通过它的[readme]() 和[用户指南]()来获取更多信息。

## Adding React to an Existing Application `将react用于现有的项目中`

你不需要重写你的项目来使用react。

我们建议你将react用于你项目的一小部分，例如一个单独的模块，这样你就能确定它适不适合用于你的项目中。

虽然react也可以没有构建管道的情况下使用，但我们还是建议你构建一个管道，这样能提高我们的生产效率。
>现在构建管道一般有以下几个步骤：

* 一个`包管理器`，比如`yarn`或者`npm`。它能让你充分利用第三方资源，并且你能很容易安装或者更新它们。 
* 一个`打包工具`，比如`webpack`或者`Browserify`。它可以让你的代码模块化，然后将你编写的代码打包到一个小包里，优化加载时间。
* 一个`编译器`，比如`Babel`。它可以让你使用最新的javaScript代码，但仍可以运行在老版本浏览器中。

### Installing React

>`Note
        如果你安装了它，我们强烈建议你设置一个生产建立过程，来确保你在生产过程中使用的是(the fast version of React)最新的react版本`

我们推荐使用`yarn`或者`npm`来管理前端依赖。如果你不熟悉包管理器，这里有一个很好的[yarn文档](https://yarnpkg.com/en/docs/getting-started)来帮助你。

>使用`yarn`安装React，执行如下命令：
```javascript
yarn init
yarn add react react-dom
```
>使用`npm`安装React，执行如下命令
```javascript
npm init
npm install --save react react-dom
```
yarn和npm下载的react包都来自[npm注册表](https://www.npmjs.com/)

### Enabling ES6 and JSX

我们建议您使用[Babel](http://babeljs.io/)来让你能在javascript代码中使用ES6和JSX。ES6是javaScript的新特性，让你的开发更加轻松。JSX是javaScript语言的一种扩展，能很好的配合react，让你获得更优的开发体验。

[Babel配置说明](https://babeljs.io/docs/setup/)介绍了如何在不同的环境下配置Babel。确认一下你已经安装过`babel-preset-react`，还有`babel-preset-env`，并且确保它们在你的`.babelrc`这个配置文件中。让我们继续。

### Hello World with ES6 and JSX

我们建议您使用打包工具，如`webpack`或者`Browserify`。它可以让你的代码模块化，然后将你编写的代码打包到一个小包里，优化加载时间。

>这儿有一个react的小例子：

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(
    <h1>Hello,world!</h1>,
    document.getElementById('root')
);
```

这段代码呈现在一个id为"root"的DOM元素里，所以你的HTML文件里需要一个这样的元素`<div id="root"></div>`。

同样，你也可以在你的现有的用任何javscript UI组件库编写的应用程序里的，随便哪儿的DOM元素中渲染一个react组件。

[Learn more about integrating React width existing code。]()

### Development and Production Versions

React默认包含许多有帮助的警告⚠️。这些警告在我们的开发过程中非常有用。

`不过，这些警告让我们的React开发版本更大，更慢，所以当你要部署app时，请使用线上版本。`

>了解[how to tell if your website is serving the right version of React`如何判断你的网站是否提供正确的react版本`]()。怎么建立最有效的生产流程：

* [使用`create react app`来创建生产版本]()
* [使用`Single-File Builds`来创建生产版本]()
* [使用`Brunch`来创建生产版本]()
* [使用`Browserify`来创建生产版本]()
* [使用`Rollup`来创建生产版本]()
* [使用`webpack`来创建生产版本]()

### Using a CDN

>如果你不想使用npm去管理你的包，`react`和`react-dom`的npm包也支持你在`UMD`文件夹中采用single-file(单文件模式)来使用它们。如下使用CDN的例子:

```javascript
<script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
```

以上版本只适合开发，并不适用于生产。

>精简的生产版本在如下的例子里：

```javascript
<script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
```

想要使用具体的react版本，将版本中的数字替换掉就好。`例：v16.2.0 => v15.6.2`

如果你使用Bower，可以通过react包来得到react。

#### `Why the crossorigin Attribute?`为什么要有crossorigin这个属性

>如果您的react引自CDN，我们建议你去设置crossorigin属性，如下：
```javascript
<script crossorigin src="..."></script>
```

>我们建议您验证你的CDN是否设置了请求头`Access-Control-Allow-Origin: *`：

![](./imgs/cdn-cors-header.png)<br>

这将会使您在react 16及更高的版本中有更好的[错误处理体验](https://reactjs.org/blog/2017/07/26/error-handling-in-react-16.html)。