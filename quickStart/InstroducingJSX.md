# Introducing JSX `JSX介绍`

看一下下面这个变量声明：
```javascript
const element = <h1>Hello,world</h1>;
```
这个有趣的标签语句既不是字符串，也不是HTML。

它叫`JSX`，是JavaScript语言的一种扩展。我们推荐你在你的React项目中使用它来描述你期待的UI的模样。JSX可能会被你当作模板语言，但它拥有JavaScript的全部功能。

JSX创建react元素。我们在下一节`Rendering Element`会探索怎么讲这些元素渲染成DOM。以下是些必要的的JSX基础知识。

## Why jsx?

React坚信渲染逻辑就是与别的UI逻辑的耦合：事件怎么处理、状态怎么随着时间的变化而更改，还有数据是哪儿来的怎么去展示。

Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called “components” that contain both. 
// React 将重点关心的标记和逻辑以松耦合的方式放在同一个单元中，这个单元叫组件（components）。

我们会在另一部分介绍组件，如果你并不喜欢在js中添加标记，那么这个[演讲](https://www.youtube.com/watch?v=x7cQ3mrcKaY) 可能会改变你的想法。

react也可以不使用jsx，不过大多数人都发现在js代码中使用jsx，可读性更高。它也允许react显示更多有用的错误和警告。

就这些，let's get started!

## Embedding Expressions in JSX `嵌入表达式`

你可以在`{}`里嵌入各种js表达式。

例如，`2 + 2`，`user.firstName`还有`formatName(user)`这些都是有效的表达式：
```javascript
function formaName(user) {
    return user.firstName + ' ' + user.lastName;
}

const user = {
    firstName: 'Harper',
    lastName: 'Perez',
};

const element = {
    <h1>
        hello, {formatName(user)}
    </h1>
};

ReactDOM.render(
    element,
    document.getElementById('root')
);
```
[在CodePen中尝试一下](https://codepen.io/pen?&editors=0010)

为了便于阅读，我们通常将JSX分成多行。虽然这没有必要，但我们建议你给它包裹一层以防止不必要的分号插入问题。

## JSX is an Expression Too (jsx也是一个表达式)

编译完成后，JSX表达式成为了一个常规的js函数调用，并被定义为一个javaScript对象。

这意味着，你可以在`if声明`和`for循环`中使用JSX，把它做为变量，做为函数的参数，以及做为函数返回值：

```javascript
function getGreeting(user) {
    if (user) {
        return <h1>Hello, {formatName(user)}!</h1>
    }
    return <h1>Hello, Stranger.</h1>
}
```

## Specifying Attributes with JSX （在属性中使用jsx表达式）

你可能用引号引起来的字符串做为属性值：

```javascript
const element = <div tabIndex="0"></div>;
```

你也会用{}（花括号）包裹的javascript表达式来做为属性值：

```javascript
const element = <img src={user.avatarUrl}></img>;
```

当在一个属性中使用javascript表达式时，请不要给在花括号外再用分号包裹。要么使用分号要么使用花括号，但绝对不要同时使用它们两个。

>> 注意⚠️：
        由于JSX比HTML更接近JavaScript，React DOM 使用 camelCase属性命名规范来替代HTML属性名称。<br/><br/>
        比如，`class`在JSX中写为`className`,还有`tabindex`在jsx中变成了`tabIndex`。

## Specifying Children with JSX

如果为空标签，你必须立即使用“/>“做为结束标识。就像XML:

```javascript
const element = <img src={user.avatarUrl} />;
```

JSX标签可以包含子元素：

```javascript
const element = (
    <div>
        <h1>Hello!</h1>
        <h2>Good to see you here.</h2>
    </div>
);
```

## JSX Prevents Injection Attacks (jsx防止注入攻击)

在JSX中嵌入用户输入还是蛮安全的：

```javascript
const title = response.potentiallyMaliciousInput;
// This is safe
const element = <h1>{title}</h1>;
```

默认情况下，React DOM避开了在渲染元素前获取JSX嵌入的值。这可以确保，你无法在你的应用注入任何不明确的文字。所有的东西在渲染前都会被转成字符串。这样可以帮我们避免XSS攻击。

## JSX Represents Objects

Babel 将 JSX 编译成 React.createElement()。

这两个例子是一样的：

```javascript
const element = (
    <h1 className="greeting">
        Hello, world!
    </h1>
);
```

```javascript
const element = {
    type: 'h1',
    props: {
        className: 'greeting',
        children: 'Hello, world',
    }
};
```

React.createElement()执行一些检查帮你编写无错的代码，但实际上，它创建了一个这样的对象：

```javascript
const element = {
    type: 'h1',
    props: {
        className: 'greeting',
        children: 'Hello, world'
    }
};
```

这个对象叫做react元素。你可以理解为你在屏幕上看到的东西的一种描述。react读取这些对象，并且用它们创建DOM元素以使他们保持最新的状态。

我们将在下一章节研究是怎么给这些react元素渲染成DOM的。

>> 提示
        我们建议你在你的编译器中使用babel，这样es6代码和jsx语法都能正确地高亮显示。这个站点使用[Oceanic Next颜色方案](https://labs.voronianski.com/oceanic-next-color-scheme/)，能很好的兼容两者。        
