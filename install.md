# Installation安装
=====================================
\<br>\<br>
>> react是一个灵活的框架，可被用于各种项目。你可以用它创建一个新的应用，你也可以逐渐地将它引入到现有的代码库中，无需再进行重写。

>> here are a couple of ways to get start `这儿有几种方式供你去开始使用它`
---------------------------------------------------------------------------
* try react
* create a new app
* Add react to an existing app
-----------------------------------------
## trying out react 
---------------------
>>如果你仅仅是尝试它，你可以使用codepen。尝试从这个小例子开始（hello world）。你不需要安装任何东西，你可以轻易地修改代码然后看它的效果。

如果你更喜欢用自己的编辑器，你同样也可以下载这个文件，编辑它，然后用你的浏览器中打开它。这是一个很慢很慢的代码改变的过程，所以不要将它用于生产。

如果你想用它做一个正式的应用，这里有两个更受欢迎的打开方式：使用create-react-app，或者将它添加到一个现有的应用上。

create a new app

Create react app 是最好的方式去创建一个单页react应用。它帮你搭好了开发环境便于你以后使用javascript，提供一个些非常棒的开发者经验，充分利用你的app去生产。

npm install -g create-react-app  //全局安装create-react-app
create-react-app my-app //创建名为my-app的项目

cd my-app 
npm start //运行

Create react app 并没有处理后端逻辑和数据库；它仅仅创建了一个前端工程，所以你能用它搭配任何后台系统，只要你想。它使用打包工具如bable，webpack 这些引擎，但工作的时候，无需在意这些配置。

当你准备去部署去生产时，运行npm run build 会在你的文件夹里帮你构建一个最合适的app。如果你想进一步了解create react app，你可以通过它的readme 和用户指南来获取更多信息。

adding react to an existing application
将react用于现有的项目中

你不用重写你的项目来使用react。

我们建议你将react用于你项目的一小部分，例如一个单独的模块，这样你就能看到它是不是正常运转。