# Rendering Elements`渲染元素`

元素是react应用中最小的模块。

一个元素通常描述你想要在屏幕上看到的事物：

```javascript
const element = <h1>Hello, world</h1>;
```

和浏览器的DOM元素不同，react 元素是一个简单的对象，很容易被创建。
// React DOM takes care of updating the DOM to match the React elements.
reactDOM 不停地更新DOM元素，来使它和React元素相匹配。

> 注意⚠️：<br/>
        你可能会对元素和组件感到困惑。我们下一章节会介绍`组件`。元素是组件的重要组成部分，所以我们建议你在看下一节之前将本章节读完。

## Rendering an Element into the DOM`将元素渲染成DOM`

假设你的html文件中又一个div元素

```javascript
<div id="root"></div>
```
我们称这个为root节点，因为，这里所有的东西都要被reactDOM管理。

仅用React构建出来的应用通常都有一个root节点。如果将React迁移到已有的应用里，你可能会拥有很多很多相互孤立的root节点。

将一个react元素渲染到root节点里，你需要使用ReactDOM.render():

```javascript
const element = <h1>Hello, World</h1>;
ReactDOM.render(
        element,
        document.getElementById('root');
);
```

在[codePen](https://codepen.io/gaearon/pen/rrpgNB?editors=1010)中尝试

这段代码在页面上展示“Hello, world”

## Updating the Rendered Element`更新渲染元素`

