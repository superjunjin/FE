转自 [React状态管理库及如何选择？](https://mp.weixin.qq.com/s/jrxaa3iJBb6X9tMqbmiFNw)

https://daveceddia.com/react-state-management/

前言

日常开发中常用的是哪个呢？今日前端早读课文章由@飘飘翻译分享。

正文从这开始~~

当你开始使用React时，状态的概念是比较棘手的事情之一，随着应用程序的增长，状态管理需求也会增加。

在这篇文章中，将为你介绍React中的状态管理选项，并帮助你决定在项目中使用哪一个。

## 什么是状态？

为了让我们站在同一战线上，我们先来谈谈状态。

每个交互式应用都涉及到对事件的响应，比如当用户点击一个按钮时，侧边栏就会关闭。或者有人发送了一条消息，它就会出现在聊天窗口中。

随着这些事件的发生，应用程序也会更新以反映这些事件，我们说应用的状态已经改变。应用看起来和之前不一样了，或者它在背后进入了一个新的模式。

比如，"侧边栏是打开还是关闭 "和 "聊天框中的消息 "都是状态的一部分。在编程术语中，你可能会在应用的某个地方设置一个isSidebarOpen变量为true，还有一个chatMessages数组，里面有你收到的消息。

广义上讲，在任何特定的时刻，你的应用的 "状态 "是由所有这些数据决定的。==所有这些单独的变量，不管是存储在本地组件状态还是某个第三方状态管理存储中--都是你的应用状态==。

这就是 "应用状态 "的高级概念。我们还没有谈论React特有的东西，比如useState或Context或Redux或任何东西。

## 什么是状态管理？

所有那些决定你的应用处于什么状态的变量都必须存储在某个地方。所以状态管理是一个广泛的术语，它结合了==如何存储状态和如何变更状态==。

React及其生态系统提供了很多不同的方式来存储和管理这种状态。当我说很多的时候，我的意思是LOTS。

### 存储数据

对于存储，你可以...

- 将这些变量保存在本地组件状态中--无论是使用hooks（useState或useReducer）还是类（this.state和this.setState）。
- 将数据保存在存储中，使用第三方库，如Redux、MobX、Recoil或Zustand。
- 甚至可以全局地将它们保留在Window对象上。

React不在乎你把数据放在哪里，但是...

### 更新数据和重新渲染

为了使你的应用具有交互性，你需要一种方法让React知道有什么变化，并且它应该重新渲染页面上的一些（或所有）组件。

因为尽管它的名字叫 React，但它并不像其他框架那样是"反应式"。

有些框架会 "观察 "事物，并进行相应的更新。Angular、Svelte和Vue等都做到了这一点。

==但React没有。它不会 "观察变化 "并神奇地重新渲染。你(或者其他什么)需要告诉它去做那件事==。

- 使用useState、useReducer或this.setState(类)，当你调用其中一个setter函数时，React会重新渲染。
- 如果你将数据保存在Redux、MobX、Recoil或其他存储中，那么当一些东西发生变化时，该存储将告诉React，并为你触发重渲染。
- 如果你选择在窗口window上全局保留数据，你需要告诉React在你改变该数据后更新。

哦，你要完全清楚，我不建议将你的状态全局地保存在窗口window上，因为通常来说，全局数据是要避免的。混乱的代码，难以理解等等等等。我提到这一点只是想说这是可以的，想说明React真的不在乎它的数据来自哪里 :)

### 什么时候useState不够用？

==useState钩子非常适合少量的局部组件状态==。每个useState调用都可以保存一个值，虽然你可以把这个值做成一个包含一堆其他值的对象，但最好还是把它们拆开。

（但是吧，比如同一类数据可以放到一个对象中，比如页面数据的相关数据放在一个对象一起变化）

一旦你在一个组件中超过了3-5个useState调用，事情可能会变得很难跟踪。尤其是当这些状态位相互依赖的时候。对于复杂的相互依赖关系，一个合适的状态机可能是更好的方式。（不太明白，还是没遇到过啊）

（哦，例如对一个数值的增加啊，减少啊，重置啊，等等操作。要放在一起统一管理比较清晰）

https://zh-hans.reactjs.org/docs/hooks-reference.html#usereducer

### 接下来，useReducer

从useState "向上"的下一步是useReducer。reducer函数为你提供了一个集中的地方来拦截"操作"并相应地更新状态。一个 useReducer 调用，就像 useState 一样，只能容纳一个值，==但有了 reducer，更常见的是这个单一的值是一个包含多个值的对象==。useReducer hooks让管理该对象变得更加容易。

### 用Context避免Prop Drilling 

> 就是避免爷爷爷组件到孙孙孙子组件的一层一层的向下传Prop

除了useState和useReducer之外，你很可能感受到的下一个痛点就是prop drilling。这就是当你有一个组件持有一些状态，然后向下5层的子组件需要访问它，你必须通过每一层手动prop drilling。

这里最简单的解决方案是==Context API==。它是内置在React中的。

```jsx
// Step 1: create a context. do this outside of any components,
// at the top level of a file, and export it.
export const MyDataContext = React.createContext();

// Step 2: In the component that holds the data, import that
// context and use the Provider to pass the data down
function TheComponentWithState() {
  const [state, setState] = useState('whatever');
  return (
    <MyDataContext.Provider value={state}>
      component's content goes here
      <ComponentThatNeedsData/>
    </MyDataContext.Provider>
  )
}

// Step 3: Anywhere in the subtree under the Provider, pull out
// the `value` you passed in by using useContext
function ComponentThatNeedsData() {
  const data = useContext(MyDataContext);
  // use it
}
```

尽管它很简单，但Context有一个重要的缺点，那就是性能，除非你非常小心地使用它。

==原因是当Provider的值发生变化时，每个调用useContext的组件都会重新渲染==。目前看来还不错吧？当数据改变时，组件会重新渲染？听起来不错!

但现在设想一下，如果这个值是一个包含50个不同的状态位的对象，这些状态位在整个应用程序中被使用，会发生什么情况。而且它们经常变化，而且是独立的。每当其中一个值发生变化时，使用其中任何一个值的每个组件都会重新渲染。

为了避免这个陷阱，==在每个Context中存储小块的相关数据==，并在多个Context中拆分数据（你可以拥有任意多的数据）。或者，考虑使用第三方库。

另一个要避免的性能问题是每次都向Provider的值中传递一个全新的对象。它看起来很无害，而且很容易被忽略。下面是一个例子。

(一般不会按下例这么写)

```jsx
function TheComponentWithState() {
  const [state, setState] = useState('whatever');
  return (
    <MyDataContext.Provider value={{
      state,
      setState
    }}>
      component's content goes here
      <ComponentThatNeedsData/>
    </MyDataContext.Provider>
  )
}
```

这里我们传递的是一个包含状态的对象及其 setter 的对象 setState。setState永远不会改变，state只有在你告诉它时才会改变。问题是包裹在它们周围的对象，==它将在每次TheComponentWithState被渲染时被重新创建==。

你可能会注意到，我们在这里谈论的东西并不是真正的状态管理，==而只是传递变量。这是Context的主要目的==状态本身被保存在其他地方，而Context只是把它传来传去。我推荐阅读这篇关于Context与Redux的不同之处的文章 [how Context differs from Redux](https://blog.isquaredsoftware.com/2021/01/context-redux-differences/)，以了解更多细节。

另外，查看下面的链接参考资料，了解更多关于如何用useCallback修复 "新对象 "问题。

### Learn More

- [Official docs](https://reactjs.org/docs/context.html)
- My egghead course on [React Context for State Management](https://egghead.io/courses/react-context-for-state-management)
- Context is covered in my [Pure React book](https://daveceddia.com/pure-react/) and [Pure React workshop course](https://purereact.com/)

## 第三方状态管理库

让我们来了解一下最常用的重要状态管理工具。我已经提供了链接来了解每个工具的详细信息。

### Redux

在这里提到的所有库中，Redux存在的时间最长。它遵循的是函数式（如函数式编程）的风格，严重依赖不变性[immutability](https://daveceddia.com/react-redux-immutability-guide/)。

你将创建一个单一的全局存储来保存应用程序的所有状态。一个**reducer**函数将接收你从组件中派发（**dispatch**）的动作（**actions**），并通过返回一个新的状态副本来响应。

因为更改只通过动作发生，所以可以保存和重放这些动作，并到达相同的状态。你也可以利用这一点来==调试生产中的错误==，像[LogRocket](https://logrocket.com/)这样的服务存在，通过记录服务器上的动作来实现这一目的。

#### 优点

- 自2015年以来一直处于试验阶段
- 官方的[Redux Toolkit](https://redux-toolkit.js.org/)库减少了模板代码。
- 优秀的开发工具让调试变得简单
- Time travel调试
- bundle size小（redux+react-redux约为3kb）。
- 功能性的风格意味着很少有幕后隐藏的东西
- 有自己的库生态系统，用于做一些事情，如同步到localStorage，管理API请求，以及更多。

#### **缺点**

- 心智模型需要一些时间来理解，特别是当你不熟悉函数式编程的时候
- 对不可变性的严重依赖会使编写reducer变得很麻烦(通过添加 [Immer](https://github.com/immerjs/immer)库，或使用包含Immer的[Redux Toolkit](https://redux-toolkit.js.org/)来缓解这一问题)
- 要求你对所有的事情都要明确（这可能是赞成或反对，取决于你喜欢什么）。

#### Learn More

- [Redux Docs](https://redux.js.org/)
- My free [Redux Tutorial](https://daveceddia.com/redux-tutorial/)
- My paid course [Pure Redux](https://daveceddia.com/pure-redux/)

### MobX

MobX可能是内置Context API之外最流行的Redux替代品。Redux是关于显式和功能的，而MobX则采用了相反的方法。

MobX是基于==观察者/可观察模式的==。你将创建一个可观察的数据模型，将你的组件标记为该数据的 "观察者"，MobX将自动跟踪它们访问哪些数据，并在数据变化时重新渲染它们。

它让你自由地定义你认为合适的数据模型，并给你提供工具来观察该模型的变化并对这些变化做出反应。

MobX在幕后使用ES6 Proxies来检测变化，所以更新可观察的数据就像使用普通的赋值操作符`=`一样简单。

#### **优点**

- 以真正的 "反应式 "方式管理状态，因此当你修改一个值时，任何使用该值的组件都会自动重新渲染。

- 不需要任何actions或者reducers，只需修改你的状态，应用程序就会反映出来。

- 神奇的反应性意味着写更少的代码。

- 你可以编写常规的可变性代码。不需要特殊的setter函数或不可变性immutability。

#### **缺点**

- 不像Redux那样广泛使用，所以社区支持较少（教程等），但在用户中深受喜爱
- 神奇的反应性意味着更少的明文代码。(这可能是一个优点或缺点，取决于你对自动更新 "魔法 "的感觉)
- 要求使用ES6 Proxies，意味着不支持IE11及以下版本。(如果你的应用需要支持IE，那么旧版本的MobX可以不需要Proxies)

#### Learn More

- Official [Intro to MobX and React](https://mobx.js.org/getting-started.html)
- [Mobx on Github](https://github.com/mobxjs/mobx)
- Free [MobX video course on egghead](https://egghead.io/courses/manage-complex-state-in-react-apps-with-mobx) by its creator Michel Weststrate

### MobX状态树

MobX状态树（或MST）是在MobX之上的一层，它给你提供了一个==反应式的状态树==。你将使用MST的类型系统创建一个类型化的模型。模型可以有视图（计算属性）和动作（setter函数）。所有的修改都要经过动作，因此MST可以跟踪发生了什么。

下面是一个模型的例子。

```js
const TodoStore = types
  .model('TodoStore', {
    loaded: types.boolean,
    todos: types.array(Todo),
    selectedTodo: types.reference(Todo),
  })
  .views((self) => {
    return {
      get completedTodos() {
        return self.todos.filter((t) => t.done);
      },
      findTodosByUser(user) {
        return self.todos.filter((t) => t.assignee === user);
      },
    };
  })
  .actions((self) => {
    return {
      addTodo(title) {
        self.todos.push({
          id: Math.random(),
          title,
        });
      },
    };
  });
```

模型是可观察的，这意味着如果一个组件被标记为MobX观察者，当模型变化时，它将自动重新渲染。你可以将MST与MobX结合起来，不需要太多的代码就能写出反应式组件。

MST的一个很好的用例是存储领域模型数据。它可以表示对象之间的关系（例如TodoList有很多Todos，TodoList属于一个User），并在运行时执行这些关系。

变更是以==补丁流==的形式创建的，你可以保存和重新加载整个状态树或其部分的快照。两个用例：在页面重载之间将状态持久化到本地存储，或将状态同步到服务器。

#### **优点**

- 类型系统保证了你的数据将是一个一致的形状。

- 自动跟踪依赖关系意味着MST可以智能地只重新渲染需要渲染的组件。
- 变更是以颗粒状补丁流的形式创建的。
- 简单地对整个或部分状态进行可序列化的JSON快照。

#### **缺点**

- 你需要学习MST的类型系统。
- 魔力与显性的权衡

- 补丁、快照和动作的一些性能开销。如果你的数据变化非常快，MST可能不是最合适的。

#### Learn More

- [mobx-state-tree on Github](https://github.com/mobxjs/mobx-state-tree)
- Official [Getting Started Tutorial](https://mobx-state-tree.js.org/intro/getting-started)
- Free [MobX State Tree course on egghead](https://egghead.io/courses/manage-application-state-with-mobx-state-tree) by the creator

### Recoil

Recoil是这个列表中最新的库，由Facebook创建。它可以让你把数据组织成一个图形结构。==它有点类似于MobX状态树，但前期没有定义一个类型化的模型==。它的API就像React的useState和Context API的组合，所以感觉和React很相似。

要使用它，你将你的组件树包裹在一个RecoilRoot中（类似于你使用自己的Context Provider的方式）。然后在顶层创建状态的 "原子"，每个原子都有一个唯一的键。

```jsx
const currentLanguage = atom({
  key: 'currentLanguage',
  default: 'en',
});
```

然后，组件可以使用useRecoilState hook来访问这个状态，它的工作原理与useState非常相似。

```jsx
function LanguageSelector() {
  const [language, setLanguage] = useRecoilState(currentLanguage);

  return (
    <div>Languauge is {language}</div>
    <button onClick={() => setLanguage('es')}>
      Switch to Español
    </button>
  )
}
```

还有一个 "选择器 "的概念，它可以让你创建一个原子视图：想一想派生状态，比如 "TODO的列表过滤到只剩下已完成的那些"。

通过跟踪对useRecoilState的调用，Recoil可以跟踪哪些组件使用了哪些原子。这样它就可以在数据发生变化时，只重新渲染那些 "订阅 "某项数据的组件，所以这种方法在性能方面应该可以很好地扩展。

#### 优点

- 与 React 非常相似的简单 API
- 它被Facebook用在他们的一些内部工具中。
- 为性能而设计
- 可与React Suspense一起工作，也可不与React Suspense一起工作（在撰写本文时，React Suspense仍在试验阶段）。

#### **缺点**

- 这个库成立才几个月，所以社区资源和最佳实践还没有其他库那么强大。

### React-Query

React-Query与列表中的其他库不同，因为它是一个获取数据的库，而不是一个状态管理库。

我把它放在这里，是因为通常情况下，应用程序中的状态管理有很大一部分是围绕着加载数据、缓存、显示/清除错误、在正确的时间清除缓存（或者在没有清除的时候遇到bug）等等......而react-query很好地解决了所有这些问题。

#### 优点

- 将数据保存在每个组件都能访问的缓存中。
- 可以自动重新获取(停滞-同时-验证、窗口重新聚焦、轮询/实时)
- 支持获取分页数据
- 支持 "加载更多 "和无限滚动数据，包括滚动位置恢复。
- 你可以使用任何HTTP库（fetch，axios等）或后端（REST，GraphQL）。
- 支持React Suspense，但不要求它。
- 并行+依赖性查询
- 突变+反应式重取（"在我更新这个项目后，重取整个列表"）。
- 支持取消请求
- 用自己的React Query Devtools进行良好的调试。
- bundle尺寸小（6.5k minified + gzipped）。

#### **缺点**

- 如果你的要求很简单，可能会矫枉过正。

#### Learn More

- [react-query on Github](https://github.com/tannerlinsley/react-query)
- This [conference talk by the creator](https://youtu.be/seU46c6Jz7E)
- Plenty of [examples in the docs](https://github.com/tannerlinsley/react-query#examples)

### XState

最后一个也不是真正意义上的状态管理库，和这个列表中的其他库一样，但它非常有用！

XState用JavaScript（和React，但它可以与任何框架一起使用)）实现了**状态机**和状态图表。状态机是一个 "众所周知 "的想法（在学术文献的意义上），已经存在了几十年，它们在解决棘手的状态问题方面做得非常好。

当很难推理出一个系统可以采取的所有不同组合和状态时，状态机是一个很好的解决方案。

举个例子，想象一个复杂的自定义输入，比如Stripe公司的那些花哨的信用卡号码输入--这些输入能够精确地知道什么时候在数字之间插入空格，以及将光标放在哪里。

现在想想：当用户点击右键时，你应该怎么做？嗯，这取决于光标的位置。而这取决于框中的文字是什么(光标是否在我们需要跳过的空格附近?没有?)。而且也许他们按住Shift键，你需要调整所选区域......有很多变量在起作用。你可以看到这将如何变得复杂。

手工管理这种事情是很棘手的，而且容易出错，因此使用状态机，你可以列出系统可能处于的所有状态，以及它们之间的转换。XState将帮助你做到这一点。

#### 优点

- 简单的基于对象的API来表示状态和它们的转换。
- 可以处理复杂的情况，如平行状态
- [XState Visualizer](https://xstate.js.org/viz/)对于调试和步入状态机真的很不错。
- 状态机可以大幅简化复杂的问题。

#### **缺点**

- 用状态机思考 "需要适应一下
- 状态机描述对象可能会变得相当啰嗦（但是，想象一下，用手写它

#### Learn More

- [Official docs](https://xstate.js.org/)
- free [video course on egghead](https://egghead.io/courses/introduction-to-state-machines-using-xstate)

## "X怎么办？"

还有很多库我在这里没有篇幅介绍，比如Zustand、easy-peasy等。不过可以看看这些，它们也不错：)

## 学习状态管理的技巧

小例子对学习很有好处，但往往会让一个库显得矫枉过正。("谁需要Redux来做TODO列表?" "为什么你要为一个模态对话框使用整个状态机？")

大的例子很适合将一件事付诸实践，但作为介绍往往让人觉得太难。("哇，这些状态机的东西看起来太复杂了")

就我个人而言，当我刚开始接触一件事情的时候，我会先从那些 "愚蠢 "的小例子开始，即使我真正的目标是更大的事情。我发现现实世界的例子很容易让人迷失在草丛中。

祝你在自己的状态管理之路上好运：)