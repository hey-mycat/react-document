# Components and Props

// Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.

component 类似于 javascript的函数。接受任意的输入（叫做props）并且返回将要在页面上展示的react元素。

## Functional and Class Compontents 纯函数组件和类组件

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

类组件会附带一些额外的特性，我们会在下节介绍。现在，先来了解一下纯函数组件的简洁。

## Rendering a Component 渲染一个组件

此前的示例里，我们只见到过react元素表示DOM元素，就像这样：

```javascript
const element = <div />;
```

然而，react元素也可以表示用户自定义组件：

```javascript
const element = <Welcome name="Sara" />
```

react会把jsx属性做为Props对象来传递给自定义组件。

下面这段代码会在页面上渲染“Hello, Sara”:

```javascript
function Welcome(props) {
    return <h1>Hello, {props.name}</h1>
}

const element = <Welcome name="Sara" />;
ReactDOM.render(
    element,
    document.getElementById('root')
);
```

在[codepen](https://codepen.io/pen?&editors=0010)中尝试这段代码

让我们看下这个例子都做了什么：
1. 我们定义了一个带有<Welcome name="Sara" />的ReactDOM.render()函数
2. React调用Welcome组件，并将{name: 'Sara'}这个对象做为rops传递给Welcome组件。
3. 我们的Welcome组件返回了\<h1>Hello, Sara\</h1>这个元素
4. React DOM很快将这个元素渲染到页面上。

> ⚠️：
        所有组件的首字母都要大写。<br/><br/>
        react会将小写字母开头的组件解读为DOM标签。比如，<div />表示一个HTML标签，而<Welcome />表示一个组件而且要在一定范围内引用。

## Composing Components

组件可以被别的组件引用。这让我们能抽出来他们共同的部分来写一个可附用组件。在react中，一个按钮、一个表单、一个视图等都可以被写成一个组件。

比如，我们可以创建一个App组件，渲染多个Welcome组件：

```javascript
function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
}

function App() {
    return (
        <div>
            <Welcome name="Sara" />
            <Welcome name="Cahal" />
            <Welcome name="Edite" />
        </dvi>
    );
}

ReactDOM.render(
    <App />,
    document.getElementById('root')
);
```

在[codePen](https://codepen.io/pen?&editors=0010)中尝试

