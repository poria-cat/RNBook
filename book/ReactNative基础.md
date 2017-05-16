# React Native基础

本章提要
- 1.初识JSX
- 2.组件
- 3.Props和State

## 1.初识JSX
React Native抛弃了HTML，所以只好用JSX喽，在这里，我们来简单的了解一下JSX。

JSX是一个JS的语法糖，写起来就像XML。嗯，如果你不知道什么是XML的话，就脑补HTML吧，
它们都需要一些标签。比如这样：

```
<Text></Text>
```

还有这样：
```
<Image />
```
怎么样，有没有一丝熟悉的感觉？
JSX就是这样简单，我们只需要一个`<`加上组件名字和`/>`就可以了（其中Text，Image就是组件名）

## 2.组件

在React Native中，有这么几种组件，无状态组件，正常的组件和高阶组件。

>高阶组件以后补上

无状态组件，顾名思义，就是没有状态的组件，写一个无状态组件就和写一个函数一样简单。由于无状态组件的性能较高，我们
一般会在App性能优化的时候使用无状态组件。
下面是一个无状态组件的例子：

```
const Hello = () => {
    return (
        <Text>我是一个无状态组件</Text>
    )
}
```
其中，Hello是组件的名字，这里有个友情提示，在React Native中，组件的名字最好都是首字母大写，这样可以避免一些奇怪的BUG。
然后在return中写组件的内容，注意，使用文字的时候，一定要在文字外面套上Text组件，否则会红屏报错。
如果想要用Props(属性)，要传一个props参数，就像这样

```
const Hello = (props) => {...}

```
如果不知道什么是Props的话，别着急，一会儿会说到的。

接下来是正常的组件。
正常的组件能做的事情比无状态组件多了不少 (´・ω・`)。
写起来是酱紫的，稍微复杂一点：
```
class Hello extends Component {
    constructor(props) {
    super(props);
    this.state = {};
  }
    render() {
        return (
            <View>
                <Text>Hi,很高兴认识你</Text>
            </View>
        )
    }
}

```
这是一个比较完整的组件，包含了Props和State(状态)。
在正常组件中使用state和props，我们需要使用constructor来初始化一下~
这里的super(props)是为了可以在constructor使用`this.props`，
当然，如果不需要这些，则不用写（虽然没写，但是按照ES6规范，class需要有一个constructor，所以constructor会被自动加上）。就像这样：

```
class Hello extends Component {
    render() {
        return (
            <View>
                <Text>略略略/Text>
            </View>
        )
    }
}
```

## 3.Props和State

嗯哼，刚才稍微提了一下Props和State，是不是很想知道这俩是啥嘞~
别着急，我这就说(´・ω・`)
Props的意思是属性，在React中，我们可以实现组件的复用(毕竟不复用组件太浪费了)。为了实现
组件的复用，我们希望可以对组件做些定制，这个时候，我们就需要使用Props了。往组件中传些不同的参数，从而使组件具有不同的功能。我们称这些
参数为Props。如果不太理解，没关系，来看这个栗子。

设计师为衣服厂设计了一些衣服，但是为了照顾到不同的人群，所以要有不同的型号。高的，矮的，胖的，瘦的。虽然有不同的型号，但是
是同一款衣服，我们可以认为高矮胖瘦是参数，衣服的款式是一个组件。

我们来看一下Props怎么用。首先写一个叫做Eat的组件：

```
class Eat extends Component {
    render() {
        return (
                <Text>我想吃</Text>
        )
    }
}

```

在组件里使用Props，我们需要一对花括号`{}`(写其他的JS语句也需要花括号)就像这样:

```
return (
    <Text>我想吃{this.props.food}</Text>
)
```

在props后面跟着的是属性的名字

接下来，我们写另一个组件Dinner，并引入Eat组件：

```
class Dinner extends Component {
    render() {
        return (
                <Eat />
        )
    }
}
```

然后使用props:

```
<Eat food='鱼' />
```

这样最终会显示我想吃鱼，这里的鱼是food的值。到这里，Props的栗子就结束了，我们来看看State。

一般来说，组件是需要和用户进行交互的，组件会随着随着交互而发生变化，这里的变化指的是State也就是状态。

下面是一个用到了状态的组件:

```
class NeedState extends Component {
    constructor(props) {
    super(props);
    this.state = { text: '' };
  }
    render() {
        return (
            <View>
                <Text onPress={() => { this.setState({ text: '状态变了' })} }>点我！</Text>
                <Text>期待会发生的事情</Text>
            </View>
        )
    }
}
```

首先，我们需要constructor函数来初始化状态，别忘记用`this.state`写入状态的名字。`onPress`可以帮我们在点了某个组件之后
执行一定的动作。我们在这里用它来触发`setState`来改变状态。

如果没有什么奇怪的错误的话，点击`点我`这个文本之后，下面的文字会变成`状态变了`。

State大概就是这么用的，没什么难度。在使用React Native的过程中，我们会时常用到Props和State，所以记下它们的用法还是很有必要的。