# Rendering Elements`渲染元素`

元素是react应用中最小的模块。

一个元素通常描述你想要在屏幕上看到的事物：

```javascript
const element = <h1>Hello, world</h1>;
```

和浏览器的DOM元素不同，react 元素是一个简单的对象，很容易被创建。
// React DOM takes care of updating the DOM to match the React elements.
reactDOM 不停地更新DOM元素，来使它和React元素相匹配。

> 提示⚠️：<br/>
        你可能会对元素和组件感到困惑。我们下一章节会介绍`组件`。元素是组件的重要组成部分，所以我们建议你在看下一节之前将本章节读完。

## Rendering an Element into the DOM`将元素渲染成DOM`

假设你的html文件中又一个div元素

```javascript
<div id="root"></div>
```
我们称这个为root节点，因为，这里所有的东西都要被reactDOM管理。

仅用React构建出来的应用通常都有一个root节点。如果将React迁移到已有的应用里，你可能会拥有很多很多相互孤立的root节点。

将一个react元素渲染到root节点里，需要将这两者都传递给ReactDOM.render():

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

react元素是不可变的。一旦你创建了一个react元素，你不能去更改它的子元素和属性。一个React元素就像是一部电影里面一帧一帧的画面，是相互独立的。它就表示UI在某个状态的呈现。

唯一更新UI的方法就是创建一个新的react元素，并且将它传入ReactDOM.render()。

来，看一下这个时钟的例子：

```javascript
function tick() {
  const element = (
    <div>
        <h1>Hello, world!</h1>
        <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(
    element,
    document.getElementById('root')
  );
}

setInterval(tick, 1000);
```

在[codePen](https://codepen.io/gaearon/pen/gwoJZk?editors=0010)中尝试

这段代码每分钟在[setInterval()](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval)的回调中执行一次ReactDOM.render()。

>小提示哦😯：
    实际上，大多数react应用都只调用一次ReactDOM.render()。接下来的章节，我们将学习如何封装动态组件。<br/>
    我们建议你不要跳过这些话题，因为它们是相互依赖的。

# React Only Updates What's Necessary

ReactDOM比较新旧两个元素以及他们的子元素，只在必要的时候更新DOM，使之成为我们期待的模样。

你可以通过浏览器设置来校验一下[这段代码](https://codepen.io/gaearon/pen/gwoJZk?editors=0010)

![](https://reactjs.org/granular-dom-updates-c158617ed7cc0eac8f58330e49e48224.gif)

尽管我们每分钟都会创建一个新的React元素来描述这个UI树，但只有这个文本内容改变的时候，才会被 React DOM 更新。

// In our experience, thinking about how the UI should look at any given moment rather than how to change it over time eliminates a whole class of bugs.
据我们的经验来看，考虑所需时刻的UI应该展示什么 比 怎么去解决随着时间推移而产生的bug 要好。
