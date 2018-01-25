# State and Lifecycle

想一下之前的时钟示例。

到目前为止，我们只学到了一种更新UI的方法。

通过调用ReactDOM.render()来改变输出。

```javascript
function tick() {
    const element = (
        <div>
            <h1>Hello, world!</h1>
            <h2>It is {new Date().toLocalTimeString()}.</h2>
        </div>
    );
    ReactDOM.render(
        element,
        document.getElementById('root')
    );
}

setInterval(tick, 1000);
```

[在CodePen中尝试]()

本章，我们会学到怎样给Clock组件拆出来，使它可以真正被复用。它将会实时更新自身的状态。

我们先粗浅地给Clock拆出来：

```javascript
function Clock(props) {
    return (
        <div>
            <h1>Hello, world!</h1>
            <h2>It is {props.date.toLocalTimeString()}.</h2>
        </div>
    );
}
function tick() {
    ReactDOM.render(
        <Clock date={new Date()} />,
        document.getElementById('root')
    );
}

setInterval(tick, 1000);
```

[在CodePen中尝试]()

然儿这忽略了一个很重要的问题，时钟的更新应该由它自身来完成。

我们的期待是这样的：

```javascript
ReactDOM.render(
    <Clock />,
    document.getElementById('root')
);
```

为了实现它，我们需要向Clock组件里添加“state”。

state和props很相似，但它是组件自身控制的。

我们之前提到过用class定义的组件会带有一些额外的属性。state就是其一，一个仅存在于类中的属性。

## Converting a Function to a Class

你可以依据这五步给函数组件（Clock）转化为类组件：

1. 创建一个同样名字的class类，继承自React.Component。
2. 添加一个空的render()方法。
3. 将函数组件里的内容搬到render方法里。
4. 将props替换为this.props。
5. 删掉其余的东西

```javascript
class Clock extends React.Component {
    render() {
        return (
            <div>
                <h1>Hello, world!</h1>
                <h2>It is {this.props.date.toLocaleTimeString()}.</h2>
            </div>
        );
    }
}
```

[在CodePen中尝试]()

现在Clock是一个类组件啦。

这会儿我们就可以使用它额外的属性，比如state还有生命周期函数。

## Adding Local State to a Class
