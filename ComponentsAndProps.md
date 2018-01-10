# Components and Props

// Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.

component 类似于 javascript的函数。接受任意的输入（叫做props）并且返回将要在页面上展示的react元素。

## Functional and Class Compontents

定义组件的一个最简单的方式就是写一个javaScript函数：

```javascript
function Welcome(props) {
    return <h1>Hello,{props.name}</h1>;
}
```
这个函数是一个合法的react组件。它接收一个props对象（代表性能的参数）并返回一个react元素。我们称这种组件为“functional”，因为他们表面上就是JavaScript函数。

你也可以用ES6的类来定义一个组件：

```javascript
class Welcome extends React.Component {
    render() {
        return <h1>hello,{this.props.name}</h1>;
    }
}
```

以上两个组件代表了React的观点。

类组件会附带一下额外的属性，我们会在下节介绍。现在，先来了解一下功能组件的简洁。

## Rendering a Component

