# Installation安装
react是一个灵活的框架，可被用于各种项目。你可以用它创建一个新的应用，你也可以逐渐地将它引入到现有的代码库中，无需再进行重写。\<br>
here are a couple of ways to get start `这儿有几种方式供你去开始使用它`
* try react
* create a new app
* Add react to an existing app

## Trying out react 

如果你只是想玩玩react，你可以使用CodePen。尝试从这个示例开始：[Hello World](https://codepen.io/gaearon/pen/rrpgNB?editors=0010)。你不需要安装任何东西，你可以只改改它的代码，看看它怎么工作。\</br>

如果你喜欢用自己的文本编译器，你可以将这段代码[下载](https://raw.githubusercontent.com/reactjs/reactjs.org/master/static/html/single-file-example.html)下来，编辑它，然后在你的浏览器中打开。这是一个很慢很慢的代码改变的过程，所以不要将它用于生产。\<br>

如果你想给它用在完整的程序里，这儿有两个特别受欢迎的方式：创建一个[react应用]()，或者将它添加到你的现有的应用程序里。\<br>

## Creating a new application

创建一个react应用是开始构建一个新的react单页应用程序的最佳方式。它帮你搭好了开发环境便于你可以使用最新的javascript功能，提供非常棒的开发者体验，优化你的应用程序的生产。\</br>

>您需要在您的机器上`安装node`,版本号要大于6。\</br>

* npm install -g create-react-app  //全局安装create-react-app
* create-react-app my-app //创建名为my-app的项目

* cd my-app
* npm start //运行

>如果您安装了`npm`5.2.0以上的版本，则可以使用npx

* npx create-react-app my-app
* npm start

`create-react-app`并没有处理后端逻辑或者数据库；它仅仅创建了一个前端工程，所以你能用它搭配任何后台系统，只要你想。它使用打包工具如bable，webpack 这些引擎，但工作的时候，无需在意这些配置。

当你准备去部署去生产时，运行npm run build 会在你的文件夹里帮你构建一个最合适的app。如果你想进一步了解create react app，你可以通过它的readme 和用户指南来获取更多信息。

adding react to an existing application
将react用于现有的项目中

你不用重写你的项目来使用react。

我们建议你将react用于你项目的一小部分，例如一个单独的模块，这样你就能看到它是不是正常运转。