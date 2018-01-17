# Hello World

[在CodePen里打开这个HelloWorld的示例](https://codepen.io/pen?&editors=0010)。你无需安装任何东西，只需要打开一个选项卡，跟着我们一起去尝试这个示例就好。如果你更喜欢本地去跑你的react项目，查看 `Installation` 章节。

这有一个react的小例子：
```javascript
ReactDOM.render(
    <h1>Hello, world!</h1>,
    document.getElementById('root')
);
```
这段代码在页面上渲染一个内容为Hello，world!的标题。

接下来的几节会逐渐向你介绍怎么使用React。
// We will examine the building blocks of React apps: elements and components.
我们会检查react应用里的元素和组件。一旦你掌握它们，你就能用它们（小而能复用的部分）来构建一个复杂应用。

## A Note on JavaScript

react是一个javaScript库，所以我们假定你拥有javaScript基础。如果你觉得你不了解javaScript，我们建议你去get一下[javaScript技能](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)，以便能更好地跟着我们的文档学习react。

在这些例子里，我们也使用了一些ES6语法。但用的不多，因为它还比较新。不过我们建议你去熟悉
[箭头函数](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)、
[classes(类)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)、
[模板字面量](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)、
[let声明](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let) 以及
[const声明](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)。
你可以使用[Bable REPL](https://babeljs.io/repl/#?presets=react&code_lz=MYewdgzgLgBApgGzgWzmWBeGAeAFgRgD4AJRBEAGhgHcQAnBAEwEJsB6AwgbgChRJY_KAEMAlmDh0YWRiGABXVOgB0AczhQAokiVQAQgE8AkowAUPGDADkdECChWeASl4AlOMOBQAIgHkAssp0aIySpogoaFBUQmISdC48QA) 去看看bable对ES6代码做了怎样的转换。