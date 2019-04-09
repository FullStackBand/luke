本文部分摘自https://www.cnblogs.com/lighten/p/5931207.html

> * BPMN 代表业务流程建模符号，他是OMG维护的公共标准。它描述了业务流程分析和业务用户可用于为业务流程建模并支持流程交互，异常处理，薪酬语义等的业务友好型流程图
>  * BPMN它被商业和开源BPMS工具供应商广泛接受。它具有很强的适应性，可用于捕捉从抽象过程概述到详细过程流程到实施准备过程的所有内容。BPMN的一个主要价值主张除了是图表标准外，还有图表背后的精确语义。形状，符号（也称为标记），边界，BPMN图元素的位置以及它们的属性具有明确定义的含义，并且必须由所有工具以相同的方式进行解释。
#一、 流对象（Flow Objects）
##1.1事件（Events）
事件都是用一个圆圈来代表的，影响流程的流动，一般有一个原因（trigger）或者一个影响（result）。标准定义了三种事件：开始，中间和结束。从定义和分类名称上来看也能猜到事件的作用了，控制流程的开始，中间流转和结束，这些控制可能采取触发器（trigger）来完成，或者是导致一个结果（结束或抛出）。
1. 开始事件

|中文|英文|Trigger（原因）|Marker（标记）|
|-|-|-|-|
|开始事件|Start Event|None<br>(没有)|![](https://upload-images.jianshu.io/upload_images/13055171-332a0b89aad747c3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|条件开始事件|Conditional start event|Conditional<br>(条件句)|![](https://upload-images.jianshu.io/upload_images/13055171-49afd287be03cd92.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|消息开始事件|Message start event|Message<br>(消息)|![](https://upload-images.jianshu.io/upload_images/13055171-2ccbd8afdb41617a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|多重启动事件|Multiple start event|Multiple<br>(多重的)|![](https://upload-images.jianshu.io/upload_images/13055171-77366b65682fcdc2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|多重并行开始事件|Parallel multiple start event|Parallel Multiple<br>(多重并行)|![](https://upload-images.jianshu.io/upload_images/13055171-603376ca64e7e32d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|信号开始事件|Signal start event|Signal<br>(信号)|![](https://upload-images.jianshu.io/upload_images/13055171-033307edf00823d1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|定时开始事件|Timer start event|Timer<br>(定时)|![](https://upload-images.jianshu.io/upload_images/13055171-596f12ef7bb99523.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|

2. 中间事件

|中文|英文|Trigger（原因）|Marker（标记）|
|-|-|-|-|
|中间事件|None Intermediate Event|None|![](https://upload-images.jianshu.io/upload_images/13055171-106b893a0afaffbf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|消息事件|Message Intermediate Event|Message|![](https://upload-images.jianshu.io/upload_images/13055171-dd3210e450d9fd74.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|定时事件|Timer Intermediate Event|Timer|![](https://upload-images.jianshu.io/upload_images/13055171-cfb74bd6d2c3d0ca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|升级事件|Escalation Intermediate Event|Escalation|![](https://upload-images.jianshu.io/upload_images/13055171-9b303a721e8b5fa0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|补偿事件|Compensation Intermediate Event|Compensation|![](https://upload-images.jianshu.io/upload_images/13055171-316dc323b5619367.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|条件事件|Conditional Intermediate Event|Conditional|![](https://upload-images.jianshu.io/upload_images/13055171-6dcceef8873f3d9b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|链接事件|Link Intermediate Event|Link|![](https://upload-images.jianshu.io/upload_images/13055171-20177a96658ee518.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|信号事件|Signal Intermediate Event|Signal|![](https://upload-images.jianshu.io/upload_images/13055171-44fb04dd23ce39b7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|多重事件|Multiple Intermediate Event|Multiple|![](https://upload-images.jianshu.io/upload_images/13055171-2f8288ce6dbd3cdb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|并行多重事件|Parallel Multiple Intermediate Event|Parallel Multiple|![](https://upload-images.jianshu.io/upload_images/13055171-33114c5855cd8cce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
> 中间事件远不止这些

3. 结束事件 End Event
结束事件必须是一个顺序流的目标，不能是源头，可以有多个顺序流指向同一个结束流。一个流程可以有多个结束事件，也可以没有结束事件，但是如果存在开始事件，就必须有至少一个结束事件。如果不使用结束事件,那么所有流对象没有任何流出序列（顺序）流（即不同为一个源序列流）来标志流程过程结束。流程不会结束，直到所有的并行路径完成了。

|中文|英文|Trigger（原因）|Marker（标记）|
|-|-|-|-|
|结束事件|None End Event|None|![](https://upload-images.jianshu.io/upload_images/13055171-e03025101f06e572.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|消息结束事件|Message End Event|Message|![](https://upload-images.jianshu.io/upload_images/13055171-16b7551ff8915845.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|错误结束事件|Error End Event|Error|![](https://upload-images.jianshu.io/upload_images/13055171-c3014c06033471bc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|升级结束事件|Escalation End Event|Escalation|![](https://upload-images.jianshu.io/upload_images/13055171-c6b934773f197c94.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|取消结束事件|Cancel End Event|Cancel|![](https://upload-images.jianshu.io/upload_images/13055171-ec56cc1e6eb28cbd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|补偿结束事件|Compensation End Event|Compensation|![](https://upload-images.jianshu.io/upload_images/13055171-41d544723708482b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|信号结束事件|Signal End Event|Signal|![](https://upload-images.jianshu.io/upload_images/13055171-f65999846d9cbccd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|终止结束事件<|Terminate End Event|Terminate|![](https://upload-images.jianshu.io/upload_images/13055171-09af092fc41338bb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|多重结束事件|Multiple End Event|Multiple|![](https://upload-images.jianshu.io/upload_images/13055171-66b7812c4d7fc776.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|

##1.2活动（Activities）
1. Task 任务
task在流程中是一个原子性的活动，当流程中的作业不能被打断时task被作用一个更细级别的细节。通常，一个终端用户或者应用其执行操作变现为task形式。task对象在子流程中具有相同的形状，都是长方形有着圆角。
有三种特殊的task图标：循环、多重和补偿，一个task可能会有一个或两个这类图标。
![](https://upload-images.jianshu.io/upload_images/13055171-d7f29114a5c49cf9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
其他的task

|中文|英文|图标|
|-|-|-|
|服务任务|Service Task|![](https://upload-images.jianshu.io/upload_images/13055171-e268c423a91ab02f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|发送任务|Send Task|![](https://upload-images.jianshu.io/upload_images/13055171-a3b361d01a45eb04.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|接收任务|Receive Task |![](https://upload-images.jianshu.io/upload_images/13055171-2272e49ac3003f9e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|用户任务|User Task  |![](https://upload-images.jianshu.io/upload_images/13055171-507b8954273fa8ef.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|手工任务|Manual Task |![](https://upload-images.jianshu.io/upload_images/13055171-383c17a32d8582cb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|业务规则任务|Business Rule Task |![](https://upload-images.jianshu.io/upload_images/13055171-c0098bf73227d104.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|脚本任务|Script Task |![](https://upload-images.jianshu.io/upload_images/13055171-1ae0d68d47024f58.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
这些任务中，需要人参与自身完成的有Manual Task 和UserTask。Manual Task是一个不受任何商业流程引擎管理的任务，User Task是。不受管理即意味着流程引擎无法追踪器任务的开始和完成。举个例子，这个可能就是一张充满指令的纸，为电话技术人员帮顾客安装电话
2. Sub-Processes 子流程 
子流程是一个活动的内部细节建模，使用活动、事件和网关以及序列流。子流程是流程内部的一个图形对象，但是它也能够被打开来展现更低一层的流程。子流程定义了一个上下文范围，可用于属性可见性、事务的范围，异常处理，事件或者是补偿。
BPMN定义了五种子流程，其中Collapsed Sub-Process可以被另外四种组合取代。另外四种是loop、multi-instance、Compensation、Ad-Hoc。
![](https://upload-images.jianshu.io/upload_images/13055171-0cb81806479c14ab.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13055171-e0ff7e9de0146339.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
用法实例：
![](https://upload-images.jianshu.io/upload_images/13055171-704b6aed8d75d3b6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)![](https://upload-images.jianshu.io/upload_images/13055171-d79b0937457ebbf6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


3. Call Activity 调用活动
调用活动确定使用了全局流程或者全局任务的流程中的一点。调用过程用作为包装器来调用全局流程或全局任务执行中。激活调用活动将导致称为全局流程或者全局任务的控制转移。
![](https://upload-images.jianshu.io/upload_images/13055171-dfb31128de125bb9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)![](https://upload-images.jianshu.io/upload_images/13055171-974aeeeb43634b0c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13055171-c4b4fdfde2d3af90.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
调用活动必须满足数据要求，同时调用CallableElement返回数据。这意味着在活动的InputOutputSpecification中需要包含这些元素，并且必须精确的和CallableElement的元素匹配。这些元素包括：DataInputs、DataOutputs、InputSets、OutputSets。
##1.3 网关（Gateways）
网关用于控制序列流如何在一个流程中收敛和发散的交互。如果一个流程不需要控制，那么网关就是非必需的。“网关”一词意味着有一个门机制。允许或不允许通过网关——也就是说，执行到网关的时候，当网关机制被调用，输入可以被合并在一起，或者输出分离成若干部分。

|中文|英文|Trigger（原因）|Marker（标记）|
|-|-|-|-|
| 互斥网关 | Exclusive Gateway |![](https://upload-images.jianshu.io/upload_images/13055171-19ae9d94cb8ca0bb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) |
| 事件网关 | Event-Based Gateway |![](https://upload-images.jianshu.io/upload_images/13055171-8ed5beace5f80ba2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) |
| 并行事件网关 | Parallel Event-Based Gateway |![](https://upload-images.jianshu.io/upload_images/13055171-ef6b40060421aa88.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  |
| 相容网关 | Inclusive Gateway    | ![](https://upload-images.jianshu.io/upload_images/13055171-dcdfd476bec22d58.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) |
| 复杂网关 | Complex Gateway  | ![](https://upload-images.jianshu.io/upload_images/13055171-be1b643988fcb523.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
| 并行网关 | Parallel Gateway    |![](https://upload-images.jianshu.io/upload_images/13055171-2efd178c17b40c33.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) |

#二、 数据（Data）
传统的流程建模要求能够模拟物品（物理或信息的）在流程中的创建、操作和执行过程。重要的方面就是能够捕获数据的结构，并且查询或者操作结构。

BPMN本身并不提供内置的模型来描述数据结构或查询数据的语言表达式。相反，它规范hooks来允许使用外部定义的数据结构和表达式语言。此外，在同一个模型中，BPMN允许不同的数据结构和表达式语言。这些语言的兼容性和验证是在规范的范围之外，变成了工具供应商的职责。

BPMN使用XML Schema和XPath作为其默认的数据结构和表达式语言，但是供应商可以自由替换他们自己的语言。

| 中文 | 英文 | 图标 |
|-|-|-|
| 数据对象 | Data Object    |![](https://upload-images.jianshu.io/upload_images/13055171-dba7603ecea34956.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
| 集合型数据对象 | collection DataObject   |![](https://upload-images.jianshu.io/upload_images/13055171-ac9b84b803dcf70f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
| 数据存储 | Data Store    |![](https://upload-images.jianshu.io/upload_images/13055171-49c9124f2c7ca720.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
| 输入数据 | Data Input    |![](https://upload-images.jianshu.io/upload_images/13055171-24cd28d40e58905c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
| 输出 | Data Output    |![](https://upload-images.jianshu.io/upload_images/13055171-835c4975b8592a3b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
|

#三、连接对象（Connecting Objects）

| 中文 | 英文 |说明|图标 |
|-|-|-|-|
|顺序流|Sequence Flow|序列流用于显示活动将在流程中执行的顺序|![](https://upload-images.jianshu.io/upload_images/13055171-09f982e1687792b4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
|
|消息流|Message Flow|消息流用于显示准备发送和接收消息的两个参与者之间的消息流，在BPMN中，协作图中的两个独立池将表示这两个参与者|![](https://upload-images.jianshu.io/upload_images/13055171-914595561e56cd58.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
|联想|Association|关联用于将信息和构件与BPMN araphical元素链接起来。文本注释和其他工件可以与图形元素相关联。组合上的箭头指示流向|![](https://upload-images.jianshu.io/upload_images/13055171-0cc7a9f23d33ad4f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)|
#四、泳道（Swimlanes）
##1. 池子（Pools）
* 池是一个容器，与其他的池相隔离。通常用在交互流程中。池主要作用于两个独立的实体或者参与者之间的物理划分。各个池中的活动通常是有自身的流程的。因此，顺序流通常不会越过多个池，而消息流是可以的
* Pool ：池是协作参与者的图形表示(参见第112页)。它还充当“泳道”和图形容器，用于将一组活动从其他池中分区，通常是在B2B情况下。池可能以将要执行的流程的形式具有内部细节。或者池可能没有内部细节
![](https://upload-images.jianshu.io/upload_images/13055171-8c11cfef2869a594.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13055171-bd189e643a328e2a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##2. 泳道（Lanes）
* Pool的子划分，可以垂直或者水平，用来对活动的组织和分类。Lane更加接近我们传统的泳道的概念。Lane常用来将活动按照角色划分，流程可以在一个pool中跨Lane流转，但是在一个pool中一般不会这样
* Lane ： Lane是进程中的一个子分区，有时在池中，它将垂直或水平地扩展进程的整个Jength。泳道用于组织和分类活动。
![](https://upload-images.jianshu.io/upload_images/13055171-fd8e0321393ffa51.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13055171-e9a3f9c87e555e9f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#五、工件（Artifacts）
##1. 组（Group）
 将一部分元素按逻辑或特定目的进行分组，便于查看和管理，用于解释和描述目的，不会影响流程的流转
##2. 文字注释（Text Annotation）
提供一些附加性的文本信息给流程图的阅读者。
![](https://upload-images.jianshu.io/upload_images/13055171-160ccabc9321cbe1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/13055171-ab8b4e84b7d58b8a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)






