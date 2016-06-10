## 软件架构 之 概念篇

  * 本文，来自《恰如其分的软件架构－奉贤区懂的设计方法》
  * 概念 用于构建 “架构世界观”，为后续的建模提供基本元素。

### 基本概念

  1. 模块（module）：一组完成指定功能的语句，包括：输入、输出、逻辑处理功能、内部信息、运行环境（与功能对应但不是一对一关系）。
  2. 组件（component）：系统中相当重要的、几乎是独立的可替换部分，它在明确定义的构架环境中实现确切的功能。
  3. 模式（pattern）：指经过验证，至少适用于一种实用环境（更多时候是好几种环境）的解决方案模板（用于结构和行为。在 UML中：模式由参数化的协作来表示，但 UML 不直接对模式的其他方面（如使用结果列表、使用示例等，它们可由文本来表示）进行建模。存在各种范围和抽象程度的模式，例如，构架模式、分析模式、设计模式和代码模式或实施模式。模式将可以帮助我们抓住重点。构架也是存在模式的。比如，对于系统结构设计，我们使用层模式；对于分布式系统，我们使用代理模式（通过使用代理来替代实际的对象，使程序能够控制对该对象的访问）；对于交互系统，我们使用MVC（M模型(对象)／V视图(输出管理)／C控制器(输入处理)）模式。模式是针对特定问题的解，因此，我们也可以针对需求的特点采用相应的模式来设计构架。
  4. 构架模式（architectural pattern）：表示软件系统的基本结构组织方案。它提供了一组预定义的子系统、指定它们的职责，并且包括用于组织其间关系的规则和指导。
  5. 层（layer）：对模型中同一抽象层次上的包进行分组的一种特定方式。通过分层，从逻辑上将子系统划分成许多集合，而层间关系的形成要遵循一定的规则。通过分层，可以限制子系统间的依赖关系，使系统以更松散的方式耦合，从而更易于维护。（层是对构架的横向划分，分区是对构架的纵向划分）。
  *以上来自：[架构设计的方法学](http://blog.csdn.net/zhongguoren666/article/details/7001366)*

  *“分层”属于“分治、分割”，后面在建模中去说*

### 概念关系