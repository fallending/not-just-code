## 讨论 iOS 应用架构

“维基百科上有个专门的页面，上面罗列了常见的形式逻辑错误和非形式逻辑错误。但实际上，导致人们犯下这些逻辑错误的最重要的原因只有两个：概念不清，拒绝接受不确定性。” —— 李笑来。

所以，我们要理清各种概念，而有关架构这档子事儿，概念很多。

### 思想：分层、隔离、解耦

1. 分层：UI层、逻辑层、数据层

2. 隔离

3. 解耦：
  > 解耦是代码解耦，也为复用提供可能，也是给人解耦。

4. [模块与组件](https://github.com/BinaryArtists/not-just-code/blob/master/ios/architect/modularize.md)

### 模式：架构模式、设计模式

1. 架构模式

2. 设计模式

### 优秀框架的特征

  1. 重用
    > 为了避免重复劳动，降低成本。重用是框架实现中的最为核心的目标，提高复用度是框架的首要目的。
    > 层次分明，高度组件化，框架中的各个部件高度独立。
    > 部件细化，性能高效，内存占用率低。
    > 耦合度低（可拆可组）

  2. 高效
  3. 安全
    > 运行安全稳定，可以通过完善TDD测试机制来保障。

  4. 可扩展
  5. 简明
    > 一个复杂的架构，不论是测试，还是维护，都是困难的。

  6. 透明
    > 边界清晰，隐藏细节，暴露接口。
    > 提高了使用者效率，降低了学习的门槛。

### 框架设计的指导原则

  1. 概要框架总体功能目的 
  2. 对框架总体功能目的进行细化，分层（层次之间相对独立，互不干涉），仔细斟酌，理清层次之间的依赖关系（如，核心层，中间层，应用层）。    
    * 核心层：处于最低层，不依赖于框架中的其它层；
http://www.cnblogs.com/eugenewu0808/archive/2008/12/25/1362128.html    
    * 中间层：根据具体 框架 的需要自行定义，取名，注意理清层次之间的依赖关系；
http://www.cnblogs.com/eugenewu0808/archive/2008/12/25/1362123.html    
    * 应用层：在核心层以上，依赖于核心层；
http://www.cnblogs.com/eugenewu0808/archive/2008/12/25/1362122.html 
  3. 从核心层开始，逐层细化各个部件，仔细推敲部件名称，构思部件的功能，合理归类。

### 实施手段：模块化、组件化、服务化、插件化



### 流行的架构模式

  * MVC
    1.

  * MVVM
    1.
    2. 单页面交互模型, ![mvvm-single-view-model](https://github.com/BinaryArtists/not-just-code/blob/master/ios/imges/mvvm-single-view-model.png)
    3. ViewModel的责任（它其实就是个打杂的，可测试，但他的责任与“ViewModel”并不搭配。）
      * 用户输入数据验证
      * 网络数据获取
      * view数据处理（mapping a model value to a formatted string ）
      * VC的跳转控制逻辑（视图逻辑）
      * 数据绑定（RAC）
      * 数据变化通知（update）

  * MVP
    1.
    2. 单页面交互模型, ![mvp-single-view-model](https://github.com/BinaryArtists/not-just-code/blob/master/ios/imges/mvp-single-view-model.png)

  * VIPER（View, Interactor, Presenter, Entity, Routing），并且，他的陈述者提到了[简明架构](http://blog.8thlight.com/uncle-bob/2012/08/13/the-clean-architecture.html)
    1. [Architecting iOS Apps with VIPER](http://www.objc.io/issue-13/viper.html), ![image](https://github.com/BinaryArtists/not-just-code/blob/master/ios/imges/2014-06-07-viper-wireframe-76305b6d.png)
    2. VIPER 的核心在于它是建立在单一责任原则上的架构
    3. 视图：根据展示器的要求显示界面，并将用户输入反馈给展示器。
    4. 交互器：包含由用例指定的业务逻辑。
    5. 展示器：包含为显示（从交互器接受的内容）做的准备工作的相关视图逻辑，并对用户输入进行反馈（从交互器获取新数据）。
    6. 实体：包含交互器要使用的基本模型对象。
    7. 路由：包含用来描述屏幕显示和显示顺序的导航逻辑。

    8. *不做过多的逻辑，不同意把“single responsibility”用在架构分层上，粒度太细，内聚很差。*

  * MVCS 1 （service）
    1. A complete system may look like this: -- (数据访问层，让Database和server对上层透明！！)
      > View Layer: Your MVC framework & code of choice
      > Service Layer: Your Controller will call this layer's objects to get or update Models, or other requests.
      > Data Access Objects: These are abstractions that your service layer will call to get/update the data it needs. This layer will generally either call a Database or some other system (eg: LDAP server, web service, or NoSql-type DB)

    2. Service layer would then be responsible for:
      > Retrieving and creating your 'Model' from various data sources (or data access objects).
      > Updating values across various repositories/resources.
      > Performing application specific logic and manipulations, etc.

  * MVCS 2 （storage）
    1. Nothing need to say.

* 然后，我们需要“理清概念”，写代码的时候，那些代码做了什么事，属于架构的哪一环，也就是要知道他的“责任”。
*

### 混合框架

[]()

### 根据特性来选用架构

  * 特性：
    1. 可测试
    2. 可扩展

  * 分析
    1. (可测试、)：UI测试，业务测试 以及更细粒度的单元测试，层次划分、模块拆分很重要，可选用：MVVM，VIPER以及变种
    2.



### 原则

  * 1. （逻辑）拆分越细越好 2. 依赖关细越少越好 3. 交互越少越好 ... 相互矛盾时，如果没有特殊理由，以优先权高者胜出。
  * 2.


### 参考

  * 1. [iOS架构设计与分层](http://www.jianshu.com/p/58040a166a10)
    > 蔡学镛：我做（开发）架构的几个原则，根据优先次序高低排列：1. （逻辑）拆分越细越好 2. 依赖关细越少越好 3. 交互越少越好 ... 相互矛盾时，如果没有特殊理由，以优先权高者胜出。
    > ![vpbd-arch-1](https://github.com/BinaryArtists/not-just-code/blob/master/ios/imges/vpbd-arch-1.png)
    > 作者在实施时变成了：![vpbd-arch](https://github.com/BinaryArtists/not-just-code/blob/master/ios/imges/vpbd-arch.png)
    > ViewController(View)：管理View的层次结构、生命周期、一些组合过的View。
    > ViewModel：负责转换View需要的数据格式。
    > Presenter：显示View、ViewController的逻辑。
    > Router(Wireframe)：页面跳转逻辑。
    > Business：核心业务逻辑，复用性很高。
    > Model：基本数据模型，根据业务来定义。
    > DataSource：对于数据的抽象，对于Business层而言，不需要知道它是从网络、数据库还是缓存中得到的。
    > 这里将presenter和viewmodel分开，其实解决了viewModel责任过杂的嫌疑: [唐巧－被误解的 MVC 和被神化的 MVVM](http://mp.weixin.qq.com/s?__biz=MjM5NTIyNTUyMQ==&mid=407454565&idx=1&sn=f2c207e30f700219d5811371b34b8cf9&scene=21#wechat_redirect)
    > 层次划分以及是否跨层依赖，基本决定团队规模和迭代速度。
    > 同层次，责任划分，绘出架构模型后，要看数据流产线有多长，架构对应着复杂度，团队规模和平均能力决定其复杂度的承受力。
    > 上面是结合外界因素分析短板，然后就要考虑架构合理性，以及它需要满足的基本特性，请看 chapter【原则】

  * 2. [简明架构](http://blog.8thlight.com/uncle-bob/2011/11/22/Clean-Architecture.html)
  * 3. [更轻量的 View Controllers](http://objccn.io/issue-1-1/)
  * 4. [测试 View Controllers](https://objccn.io/issue-13-5/)
  * 5. [使用 VIPER 构建 iOS 应用](https://objccn.io/issue-13-5/)
    > [VIPER TODO, 文章示例](https://github.com/objcio/issue-13-viper)
    > [VIPER SWIFT, 基于 Swift 的文章示例](https://github.com/objcio/issue-13-viper-swift)
    > VIPER 可以是视图 (View)，交互器 (Interactor)，展示器 (Presenter)，实体 (Entity) 以及路由 (Routing) 的首字母缩写
    >

  * 6. [Hello ZK MVVM](https://www.zkoss.org/wiki/Small_Talks/2011/October/Hello_ZK_MVVM)
  * 7. [Krush iOS Architecture](http://www.teehanlax.com/blog/krush-ios-architecture/)
    > 案例学习1: 网络层（服务器接口，CDN加速，请求队列，OAuth，请求重连机制，回调block通信机制，）
    > 案例学习2: 磁盘缓存
    > 案例学习3: 用户资料视图
    > 案例学习4: 以MVVM为主

  * 8. [Designing Rich Client Applications](https://msdn.microsoft.com/en-us/library/ee658087.aspx), [
Chapter 24: Designing Mobile Applications](https://msdn.microsoft.com/en-us/library/ee658087.aspx)
    > Figure 1 shows an overall view of typical rich client architecture, and identifies the components usually found in each layer.
    ![image](https://github.com/BinaryArtists/not-just-code/blob/master/ios/imges/IC350992.png)
    > A typical rich client application is decomposed into three layers: the presentation layer, business layer and data layer.
    >> the presentation layer:  UI and presentation logic components
    >> the business layer: business logic, business workflow and business entity components
    >> the data layer: data access and service agent components

  * 9. [The Clean Architecture](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html)
  * 10. [iOS移动端架构的那些事](http://ios.jobbole.com/84897/)
    > 讲了一般app工程开发的架构演进。

  * 11. [用Swift搭建数据驱动型iOS架构](http://mrpeak.cn/blog/swift-dda/)
    > 我们在用数据表述业务模型的时候，一般用到两种类型。一是single instance，二是collection type。single instance是单个的model实例。collection type是model实例的集合，array，set，dictionary都是属于集合类。这两者的基础变化离不开CRUD，也就是我们常说的增删改查。
    > [music4kid/Data-Driven-Architecture-Swift](https://github.com/music4kid/Data-Driven-Architecture-Swift/tree/master/TrimData)

  * 12. [iOS应用层架构之CDD](http://mrpeak.cn/blog/cdd/), [music4kid/CDD](https://github.com/music4kid/CDD)
    > 新的应用层架构方式，名之为CDD：Context Driven Design
    > 把应用层分解成三块任务：
    >> UI的展示，UI的展示通过分解UIView可以实现复杂度的分散，UI的变化则可以参考MVVM的方式，通过观察者模式（KVO）来实现。
    >> 业务的处理，业务处理为了方便管理不能分散到不同的类，反而需要放到统一的地方管理，业务代码太分散会给调试带来很大的麻烦。
    >> data flow，所有数据的变化可以在统一的地方被追踪。数据的流向单一清晰。

    > 这里作者将MVC归为应用层的分层，我认为这么理解很好，其实一个app代码，就是框架层+（应用层）：framework，data layer，business layer，UI layer。

  * 13. [Casa Taloyum iOS架构系列文章](http://casatwy.com/iosying-yong-jia-gou-tan-kai-pian.html)
  * 14. [objc.io架构系列文章](https://www.objc.io/issues/13-architecture/)
  * 15. [新浪微博iOS客户端架构与优化之路](http://blog.sina.com.cn/s/blog_68147f680102weti.html), 聊天方式的，看看就行，启发嘛，就别指望了。
  * 16. [携程移动App架构优化之旅](http://www.tuicool.com/articles/EnYzeib)，其在app端的优化，主要做了，模块化（解耦），开源框架的引用。
  * 17. [饿了么移动APP的架构演进](http://ios.jobbole.com/84148/)
   > 架构中，模块复用的第一要求便是代码的功能组件化。
   > 公有组件： 公有组件指的是封装得比较好的一些SDK，包括一些第三方组件和自己内部使用的组件。如iOS中最著名的网络SDK AFNetworking，Android下OKHttp，都是这类组件的代表
   > 业务组件，则定义为包含了一系列业务功能的整体，例如登录业务组件，注册业务组件，即为此类组件的典型代表

  * 18. [豆瓣App的模块化实践](http://www.cocoachina.com/ios/20161103/17939.html)
    > 模块化分为四个步骤，下面会分别介绍每个步骤:
    >> 1. 文件夹隔离
    >> 2. 抽象出业务无关的库
    >> 3. 拆分出公共底层模块
    >> 4. 业务模块独立
    > FRDIntent: View controller 间的解耦
    >> 在 iOS 项目，存在大量页面跳转。但 iOS 系统并不存在像 Android 的 Intent 一样的统一的页面跳转方法。在 iOS 中，处理页面跳转，需要依赖代表跳转目的页面的类，需要知道它的初始化方法。这样各个页面就需要相互依赖。这种情况对解除耦合，拆分模块很不利。为了解决这个问题，我们做了一个专门处理 iOS 中页面跳转的库：FRDIntent，并将其开源。

    >> Github地址：https://github.com/douban/FRDIntent

    > FRDIntent 有两个部分：FRDIntent/Intent 用于解决应用内的页面跳转；FRDIntent/URLRoutes，用于解决外部应用对本应用的页面调用。在使用了 FRDIntent 之后，我们很好地解除了 view controller 之间的耦合。并且为内部调用和外部调用提供了一套清晰统一的解决方案。解决了 iOS 项目中了很大一部分耦合问题：view controller 之间的耦合。为我们顺利推进模块化奠定了坚实基础。

    >> FRDIntent/Intent
    >> FRDIntent/Intent 是一个消息传递对象，用于启动 UIViewController。可以认为它是对 Android 系统中的 Intent 的模仿。当然，FRDIntent/Intent 做了极度简化。这是因为 FRDIntent/Intent 的使用场景更为简单：只处理应用内的 view controller 间跳转。

    >> 直接使用 iOS 系统方法完成各 view controller 之间的跳转，各 view controller 代码会耦合得很紧。跳转时，一个 view controller 需要知道下一个 view controller 是如何创建的各种细节。这造成了 view controller 之间的依赖。使用 FRDIntent/Intent 传递 view controller 跳转信息，可以解除 view controller 之间的代码耦合。