转自  [【译】重磅！React vs Vue 谁是 2021 年最佳 JavaScript 框架](https://juejin.cn/post/6944674279141146632)

https://dzone.com/articles/react-vs-vue-in-2021-best-javascript-framework

We’ve put together this convenient guide to help you better understand the use cases of Vue vs. React and determine which one will work best for your next project.

我们整理了这个便利的指南，以帮助您更好地理解 Vue 和 React 的使用场景，并确定哪种框架最适合您的下一个项目。

While JavaScript frameworks are now vital for web app development, many companies struggle to choose between React and Vue for their projects. The short answer is that there is no clear winner in the general React.js vs. Vue.js debate. Each framework has its pros and cons and is useful for different applications. So, we’ve put together this convenient guide to popular frameworks, to help you better understand the use cases of Vue vs. React and determine which one will work best for your next project.

因为 JavaScript 框架对 web app 开发至关重要，许多公司一直在纠结于项目中使用 React 还是 Vue。简短的答案是，没有谁明显胜出。每个框架都有其优缺点，分别适用于不同的应用程序。因此，我们整理了这个便利的指南，以帮助您更好地理解 Vue 和 React 的使用场景，并确定哪种框架最适合您的下一个项目。

## Vue.js vs. React — What Are They?

Both React and Vue are open source JavaScript frameworks that make it easier and faster for developers to build complex user interfaces. Before we get into the React vs. Vue comparison, we’ll give you a brief overview of each one.

React 和 Vue 都是开源的 JavaScript 框架，可以让开发者更容易、更快捷地构建复杂的用户界面。在对 React 和 Vue 进行比较之前，我们先对各自进行简要的概述。

The React JavaScript library offers increased flexibility by utilizing 'components,' short, isolated sections of code that developers can use to create more complex logic and UIs. React interacts with HTML documents through a 'virtual DOM,'  which is a copy of the actual DOM, but all of the elements are represented as JavaScript objects. These elements, along with React’s declarative programming style and one-way data binding, simplify and speed up development.

React 框架通过使用 ‘组件’ 提供更多的灵活性，只需一小段独立的代码，开发就可以使用它来创建更复杂的逻辑和界面。React 通过“虚拟 DOM”（真实 DOM 的副本）与 HTML 文档交互，但是所有元素都表示为 JavaScript 对象。这些元素，加上 React 的声明式编程风格和单向数据绑定，简化并加速了开发。

Vue also features two-way binding and components and uses a virtual DOM. However, Vue’s major draw is its progressive design. Vue is designed to allow developers to migrate existing projects to the framework incrementally, moving features one by one, rather than all at once. So, depending on your project’s requirements, you can use Vue as a full framework or as a lightweight library, and anything in between.

Vue 也提供了双向绑定和组件，并使用了虚拟 DOM。然而，Vue 的主要吸引力在于它的==渐进式设计==。Vue 旨在允许开发者逐步迁移现有项目到框架中，一个接一个的迁移特性，而不是一次性全部迁移。因此，根据你的项目需求，您可以将 Vue 作为一个完整的框架或者轻量级库，或者介于两者之间。

## 相同点

As you can see, Vue and React are quite similar to one another and have many of the same traits and features. The biggest similarity is the use of the virtual DOM. 

如你所见，Vue 和 React 在许多特性和功能都非常相似，最大的相似点是使用虚拟 DOM。

In addition, **both** React and Vue:

除此之外，React 和 Vue 还有如下相似点：

- Work with any existing web app.
- Suggest quite a lightweight approach for developers to quickly hop on work.
- Feature component-based architecture with lifecycle methods.
- Offer increased flexibility, speed, and performance.
- Have large, active communities.
- Offer a wide selection of libraries and tools.

- 与任何现有 web app 协同工作。
- 为开发人员提供一种轻量级的方法，让他们能够快速完成工作。
- 提供具有生命周期方法的基于组件的体系架构。
- 提供更好的灵活性、速度和性能。
- 拥有庞大而活跃的社区。
- 提供广泛的库和工具。

## 不同点

While React.js and Vue.js have many similarities, there are a few differences between the two, which have a substantial impact on what each is best suited for. The primary difference lies in the methods used by Vue vs. React for rendering content onto the DOM. Vue uses HTML templates and JSX, while React only uses JSX, which is essentially an extension that allows you to insert HTML directly into JS code. While JSX can speed up and simplify larger, more complex tasks, the downside is that it can also complicate what should be an easy task. 

尽管 React.js 和 Vue.js 有许多相似之处，但两者之间还是有一些区别，这对各自最适用于什么场景产生了重大影响。 ==二者的主要区别在于将内容渲染到到 DOM 的方法。Vue 使用 HTML 模板和 JSX，而 React 仅使用 JSX==，这实际上是一个扩展，允许您将 HTML 直接插入到 JS 代码中。 尽管 JSX 可以加快开发并简化更大、更复杂的任务，但缺点是它也可能使本来应该容易的任务变得复杂。

(对，react可能很难一眼看清楚html各个元素的位置和关系，因为插入了很多js去对html元素做处理。而vue的template可以大致清晰的理清html各个元素的位置和关系，类似原始的html)

In addition, React’s core offerings are components, DOM manipulation, and component state management. Everything else is developed and supported by the community. While seasoned developers often prefer this level of freedom, newbies may feel overwhelmed by the abundance of third-party libraries and tools. 

此外，React 的核心是提供组件，DOM 操作和组件状态管理。其他一切都是由社区开发者支持的。虽然经验丰富的开发人员通常更喜欢这种自由度，但是新手可能会因大量的第三方库和工具而感到不知所措。

While Vue has its own wide selection of community-built solutions, its core team also builds and supports commonly used tools and companion libraries, such as Vue-router, Vuex, and Vue CLI. This combination of pre-built and third-party resources helps meet the needs and desires of both beginner and senior developers alike. 

虽然 Vue 拥有广泛的社区构建方案可供选择，但其核心团队同样也构建并支持了常用工具和配套库，如 Vue-router、Vuex 和 Vue CLI。这种预构建资源和第三方资源的结合有助于满足初学者和高级开发人员的需求和愿望。

## Vue vs. React 性能

Since React and Vue share many of the same elements, their general performance is about equal. Both frameworks use virtual DOMs, and lazy loading to boost performance and page loading speeds.

由于 React 和 Vue 有许多相似点，所以它们的总体性能大致相当。这两个框架都使用虚拟 DOM 和懒加载来提高性能和页面加载速度。

However, there are certain situations where one framework clearly outperforms the other. For example, when you modify a React component state, all of the components in its subtree will re-render as well. However, in Vue, dependencies are tracked to prevent unnecessary re-renders. While you can use immutable data structures, shouldComponentUpdate, or PureComponent to prevent child component re-renders in React, this can add additional complexity and result in DOM state inconsistencies.

然而，在某些情况下，一个框架的性能明显优于另一个。例如，当你修改一个 React 组件的状态时，它的子树中的所有组件都将重新渲染。==但在 Vue 中，会跟踪依赖项以防止不必要的重新渲染==。虽然您可以使用不可变的数据结构、shouldComponentUpdate 或 PureComponent 来防止在 React 中重新渲染子组件，但这会增加额外的复杂性并导致 DOM 状态不一致。

### 1. 应用架构

React is different from other frameworks and libraries, in that it does not have a built-in architecture pattern. It uses a component-based architecture, which has its pros and cons. React UIs are rendered by components that work as functions and respond to changing data. So, the internal architecture consists of the constant interaction between the state of the components and the users’ actions.

React 与其他框架和库不同，因为它没有内置的架构模式。它使用基于组件的架构，有优点也有缺点。React UI 通过函数形式的组件渲染，并响应数据的更改。因此，内部架构由组件状态和用户操作之间的持续交互组成。

Vue’s focus on the ViewModel approach of the MVVM pattern works well for larger applications. It uses two-way data binding to connect the View and Model. The primary goal of Vue is to provide a simple, flexible view layer, not a full-blown framework.

Vue 关注的是 MVVM 模式的 ViewModel 方法，这可以很好地应用于更大的应用程序。它使用双向数据绑定来连接视图和模型。Vue 的主要目标是提供一个简单、灵活的视图层，而不是一个成熟的框架。

### 2. 可扩展性

When considering the use of React vs. Vue for large applications, React has an edge, due to its easy scalability. Since React apps solely use JavaScript, developers can utilize traditional code organization methods for easy scaling. Component reusability enhances React’s scalability.

在考虑将 React 与 Vue 用于大型应用程序时，React 具有易扩展性，因此具有优势。由于 React 应用程序仅使用 JavaScript，因此开发人员可以利用传统的代码组织方式轻松地进行扩展。组件的可重用性增强了 React 的可扩展性。

While Vue is also scalable, thanks to its wide selection of flexible tools, it is more often used in smaller applications (although the size of the app of course depends on the architecture). Due to the dynamic architecture, you will need to take advantage of Vue’s libraries and Mixin elements to overcome the scaling limitations. So if you’re considering a React vs. Vue enterprise application, React may be more accommodating of future growth.

尽管 Vue 也具有可扩展性，但由于其广泛的灵活工具选择，它更常用于较小的应用程序中（尽管应用程序的大小取决于架构）。由于采用了动态架构，因此您将需要利用 Vue 的库和 Mixin 元素来克服扩展限制。因此，如果您正在考虑使用React 还是 Vue 作为企业应用程序，React 可能会更适应未来的增长。

### 3. 文档

Vue is the clear winner when it comes to documentation. Vue’s website features excellent quality, highly-detailed descriptions, offered in multiple languages, and its docs and API references are widely regarded as the best in the industry. You can find clear answers to a number of questions and issues in the docs. However, since the Vue community is not as large as React’s, so you may have more difficulty getting the right answers to questions that are not covered in the documentation.

在文档方面，Vue 显然是赢家。Vue 的网站以卓越的质量，高度详细的描述，多语言支持，它的文档和 API 引用普遍被认为是业界最好的。您可以在文档中找到许多问题和详细的答案。但是，由于 Vue 社区不像 React 社区那么大，所以您可能很难找到文档中未涉及问题的正确答案。

React’s documentation is nowhere near the level of Vue’s, so you’ll be turning to the community a lot more often to solve challenges and issues. However, React does have a massive, active community, with a huge selection of learning materials.

React 的文档远远达不到 Vue 的水平，所以您需要更多地求助于社区去解决挑战和问题。好在 React 拥有一个庞大而活跃的社区，拥有大量可供选择的学习材料。

### 4. 社区支持

This brings us to the topic of React vs. Vue community support. This is a vital part of any technology, since the community provides assistance to both new and experienced developers and creates third-party solutions and tools.

这就引出了 React 和 Vue 社区支持的话题。这是任何技术的重要组成部分，因为社区为新开发人员和有经验的开发人员提供帮助，并创建第三方解决方案和工具。

React is developed and maintained by Facebook, which uses it in their own applications. So it has plenty of ongoing support and an active community that consistently builds and maintains new tools.

React 是由 Facebook 开发和维护的，而且 Facebook 也在自己的应用程序中使用它。因此，它拥有大量持续的支持和一个不断构建和维护新工具的活跃社区。

Vue was started by a developer, not a corporation, so it did not enjoy the immediate popularity boost that React did. In fact, when it was first released, many developers felt it was unreliable and were hesitant to adopt it. However, Vue has seen substantial growth and increase in popularity, thanks to continued support and contributions from the user community.

Vue 是由开发人员创建的，而不是一家公司，所以它没有像 React 那样迅速受到欢迎。事实上，当它第一次发布时，许多开发人员都觉得它不可靠，并犹豫是否要使用它。然而，由于用户社区的持续支持和贡献，Vue 已经有了实质性的增长并且越来越受欢迎。

### 5. 人气

毫无疑问，Vue 拥有 181K Github Star，是最受欢迎的 JavaScript 框架。但是，React 凭借 16.5 万 Star 升至第二位，并且继续增长并获得新用户。许多知名公司都有使用 Vue.js 和 React 制作的 Web 应用程序。

**Vue** 用户包括：

- Gitlab
- Euronews
- Adobe Portfolio
- Behance
- Alibaba
- Trustpilot
- Vice
- Nintendo
- BMW

**React** 用户包括：

- BBC
- Airbnb
- Facebook
- PayPal
- The New York Times
- Netflix
- Instagram
- Twitter
- WhatsApp

### 6. 安全性

Both Vue and React have their own security pitfalls, however, Vue apps are a bit easier to secure than React-based apps. While it is not possible to enable automatic protections against things like XSS vulnerabilities, Vue developers can sanitize the HTML code before implementation or utilize external libraries to help protect against attacks. In cases where you know the HTML is safe, you can explicitly render HTML content and protect the application both before and after rendering.

Vue 和 React 都有自己的安全隐患，但是，Vue 应用程序比基于 React 的应用程序更容易获得安全保护。虽然无法针对XSS 漏洞等启用自动保护功能，但 Vue 开发人员可以在实施之前对 HTML 代码进行清理或使用外部库来帮助防御攻击。 只要您知道 HTML 是安全的，则可以在渲染前后明确渲染 HTML 内容并保护应用程序。

React security relies on the developer using security best practices to protect against XSS vulnerabilities, server-side rendering attacks, SQL injections, and other threats. This may include things like using the serialize-Javascript module, exploiting script-injection flaws, and using secure React Native applications. So, while React is easy to use, it takes a lot of expertise and experience to ensure that React apps are secure.

React 安全依靠开发人员使用安全最佳实践来防御 XSS 漏洞、服务器端渲染攻击、SQL 注入和其他威胁。这可能包括诸如使用 serialize-Javascript 模块，利用脚本注入漏洞以及使用安全的 React Native 应用程序之类的东西。因此，尽管 React 易于使用，但需要大量的专业知识和经验来确保 React 应用程序是安全的。

### 7. React vs. Vue 就业市场

React’s popularity means that there is a larger pool of experienced developers to hire from. According to the 2019 Front-End Tooling survey, over 48% of developers feel comfortable using React, while only 23% claimed to be able to use Vue at a comfortable level.

React 的受欢迎程度意味着有大量的经验丰富的开发人员可供雇用。根据 2019 年前端工具调查，超过 48％ 的开发人员对使用 React 感到自在，而只有 23％ 的开发人员声称可以使用 Vue 获得舒适的开发体验。

However, HackerRank’s Developer Skills Report found that, while 33.2% of companies are looking to hire React developers, only 19% of developers have the skills that are required. Whereas 10% of companies need Vue developers, but only 5.1% of developers are qualified.

但是，HackerRank 的开发人员技能报告发现，虽然 33.2％ 的公司希望雇用 React 开发人员，但只有 19％ 的开发人员具备所需的技能。虽然 10％ 的公司需要 Vue 开发人员，但只有 5.1％ 的开发人员合格。

Vue continues to increase in popularity though, and it took fourth place in the ranking of technologies that developers wanted to learn in 2020. This growth in popularity, along with Vue’s excellent documentation and ease of learning, will likely result in an increase in qualified Vue developers.

Vue 人气持续增加，并在 2020 年开发人员想要学习的技术排名中位列第四。这种受欢迎程度的增长，加上 Vue 出色的文档和易于学习的知识，很可能会使得合格的 Vue 开发人员增加。

## 总结

To summarize, React enjoys more corporate support, greater popularity among developers, and a massive contributing community that can answer any questions you might have. It’s also easier to scale and is typically preferred for complex, enterprise-level applications.

总而言之，React 获得了更多的企业支持，在开发人员中更受欢迎，并拥有一个庞大的社区，可以回答您可能有的任何问题。它也更容易扩展，通常是复杂的企业级应用程序的首选。

While Vue, on the other hand, is not yet as widely supported and used, it is constantly increasing in popularity, due primarily to its fantastic documentation, ease of use, and incremental adoption capabilities. Vue also has more core support and a wider variety of built-in tools and solutions. When considering React vs. Vue development speed, with Vue CLI 4, it takes as little as a few weeks to set up and deliver a market-ready product.

另一方面，尽管 Vue 还没有得到广泛的支持和使用，但它的普及程度正在不断提高，这主要是因为它出色的文档、易用性和增量使用功能。Vue 还提供了更多的核心支持以及更广泛的内置工具和解决方案。当考虑 React 与 Vue 的开发速度时，使用 Vue CLI 4，只需几周时间就可以打造并交付一个符合市场需求的产品。

Clearly, both are excellent frameworks for any modern web application, and the React vs. Vue pros and cons change depending on the use-case. The right solution depends entirely on your project goals and preferences.

显然，这两种框架都是现代 web 应用程序的优秀框架，React 与 Vue 的优缺点根据使用场景而有所不同。到底使用哪一个，完全取决于您的项目目标和偏好。

**React** 是更好的选择如果您想要：

- Have a wide variety of flexible libraries, tools, and ecosystems.
- Easily use it with TypeScript, Flow, ReasonML, BuckleScript.
- Develop a highly-scalable application with easy testing and debugging.
- Quickly build a complex app.
- Create a high-performing video streaming platform or media site.
- 拥有多种灵活的库、工具和生态系统。
- 轻松地搭配 TypeScript、Flow、ReasonML、BuckleScript 使用。
- 开发一个易于测试和调试的高扩展性应用程序。
- 快速构建一个复杂的应用程序。
- 创建一个高性能的视频流媒体平台或媒体网站。

选择 **Vue** 当你想：

- Build a progressive web app or SPA.
- Start development immediately.
- Have access to more core tools and support.
- Extend an existing app’s functionality.
- 构建一个渐进式 web app 或 SPA。
- 立即开始开发。
- 获得更多的核心工具和支持。
- 扩展现有 app 的功能。

We hope this guide helps you settle the React.js vs. Vue.js debate for your next project. If you still have questions about the technologies, or you need a team of experienced developers to help create your project, send us a message using the form below!

我们希望这个指南能帮助你决定在下一个项目中使用 React.js 还是 Vue.js。如果你还有关于技术的问题，或者你需要一个有经验的开发团队来帮助创建你的项目，请使用下面的表单给我们发送消息！