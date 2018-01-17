！！！！！！！待优化
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
1. 我们定义了一个带有\<Welcome name="Sara" />的ReactDOM.render()函数
2. React调用Welcome组件，并将{name: 'Sara'}这个对象做为rops传递给Welcome组件。
3. 我们的Welcome组件返回了\<h1>Hello, Sara\</h1>这个元素
4. React DOM很快将这个元素渲染到页面上。

> ⚠️：<br/>
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

通常，新建一个react应用在最外层会有一个App组件。
//if you integrate React into an existing app, you might start bottom-up with a small component like Button and gradually work your way to the top of the view hierarchy.


## Extracting Components

不要害怕将组件拆分成更小的部分。

思考一下下面这个Comment组件：

```javascript
function Comment(props) {
    return (
        <div className="Comment">
            <div className="UserInfo">
                <img className="Avatar" 
                    src={props.author.avatarUrl}
                    alt={props.author.name}
                />
                <div className="UserInfo-name">
                    {props.author.name}
                </div>
            </div>
            <div className="Comment-text">
                {props.text}
            </div>
            <div className="Comment-date">
                {formatDate(porps.date)}
            </div>
        </div>
    );
}
```

[在CodePen中尝试](https://codepen.io/pen?&editors=0010)

这段代码接受不了一个author（对象），text（字符串）还有date（date）,用来描述一个社交网站的评论。

这个组件因为嵌套的关系可能难以改变，而且还很难复用。让我们抽出它其中的一部分写成一个组件。

首先，我们抽出来Avatar。

```javascript
function Avatar(props) {
    return (
        <img className="Avatar"
            src={props.user.avatarUrl}
            alt={props.user.name}
        />
    );
}
```

这个组件（Avatar）不需要关注他在哪条评论里被渲染。这也是我们为什么会给它一个更通用的名字（user而不是author）的原因。

我们建议你根据组件的意义来命名，而不是根据上下文随便起个名字。

现在，我们可以简化一下Comment组件了。

```javascript
function Comment(props) {
    return (
        <div className="Comment">
            <div className="UserInfo">
                <Avatar user={props.author} />
                <div className="UserInfo-name">
                    {props.author.name}
                </div>
            </div>
            <div className="Comment-text">
                {props.text}
            </div>
            <div className="Comment-date">
                {formatDate(props.date)}
            </div>
        </div>
    );
}
```

接下来，我们给UserInfo拆出来：

```javascript
function UserInfo(props) {
    return (
        <div className="UserInfo">
            <Avatar user={props.user} />
            <div className="UserInfo-name">
                {props.user.name}
            </div>
        </div>
    );
}
```

这让我们进一步简化了Comment组件：

```javascript
function Comment(props) {
    return (
        <div className="Comment">
            <UserInfo user={props.author} />
            <div className="Comment-text">
                {props.text}
            </div>
            <div className="Comment-date">
                {formatDate(props.date)}
            </div>
        </div>
    );
}
```

[在CodePen中尝试](https://codepen.io/pen?&editors=0010)

拆组件一开始是个很痛苦的过程，但在开发大型应用中很有用。你可以根据你的ui图，将不同的UI模块拆分为组件（比如按钮，面板，作者），或者他们自身足够复杂成为一个组件再好不过了。

## Props are Read-Only

绝对不能修改组件的Props!!!!!!<br/>思考这个例子:

```javascript
function sum(a, b) {
    return a + b;
}
```
这类的函数叫做[纯函数]()，它没有尝试去改变它的输入，而且，同样的输入总是对应同一个输出。

相反，下面这个函数不是纯函数，因为它修改了它的输入：

```javascript
function withdraw(account, amount) {
    account.total -= amount;
}
```



