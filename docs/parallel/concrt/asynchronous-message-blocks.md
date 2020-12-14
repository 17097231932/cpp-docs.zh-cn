---
description: 了解详细信息：异步消息块
title: 异步消息块
ms.date: 11/04/2016
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
ms.openlocfilehash: 7447d30932693eebe22d0a6f7f0aad0fba2abf16
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189140"
---
# <a name="asynchronous-message-blocks"></a>异步消息块

代理库提供多种消息块类型，使你能够以线程安全的方式在应用程序组件之间传播消息。 这些消息块类型通常用于各种消息传递例程，如 [concurrency：： send](reference/concurrency-namespace-functions.md#send)、 [concurrency：： asend](reference/concurrency-namespace-functions.md#asend)、 [concurrency：： receive](reference/concurrency-namespace-functions.md#receive)和 [concurrency：： try_receive](reference/concurrency-namespace-functions.md#try_receive)。 有关由代理库定义的消息传递例程的详细信息，请参阅 [消息传递函数](../../parallel/concrt/message-passing-functions.md)。

## <a name="sections"></a><a name="top"></a> 个

本主题包含以下各节：

- [源和目标](#sources_and_targets)

- [消息传播](#propagation)

- [消息块类型概述](#overview)

- [unbounded_buffer 类](#unbounded_buffer)

- [overwrite_buffer 类](#overwrite_buffer)

- [single_assignment 类](#single_assignment)

- [call 类](#call)

- [变压器类](#transformer)

- [choice 类](#choice)

- [联接和 multitype_join 类](#join)

- [timer 类](#timer)

- [消息筛选](#filtering)

- [消息保留](#reservation)

## <a name="sources-and-targets"></a><a name="sources_and_targets"></a> 源和目标

源和目标是消息传递中的两个重要参与者。 *源* 是指发送消息的通信终结点。 *目标* 是指接收消息的通信终结点。 你可以将源视为你从其读取的终结点，并将目标视为你写入的终结点。 应用程序将源和目标连接在一起以形成 *消息传递网络*。

代理库使用两个抽象类来表示源和目标： [concurrency：： ISource](../../parallel/concrt/reference/isource-class.md) 和 [Concurrency：： ITarget](../../parallel/concrt/reference/itarget-class.md)。 用作源的消息块类型是从派生的 `ISource` ; 作为目标的消息块类型派生自 `ITarget` 。 充当源和目标的消息块类型派生自 `ISource` 和 `ITarget` 。

[[顶部](#top)]

## <a name="message-propagation"></a><a name="propagation"></a> 消息传播

*消息传播* 是将消息从一个组件发送到另一个组件的操作。 向消息块提供消息后，它可以接受、拒绝或推迟该消息。 每个消息块类型以不同的方式存储和传输消息。 例如， `unbounded_buffer` 类存储的消息数量不受限制， `overwrite_buffer` 该类一次存储一条消息，而转换器类存储每条消息的更改版本。 本文档稍后将详细介绍这些消息块类型。

当消息块接受消息时，它可以选择执行工作，如果消息块是源，则将生成的消息传递给网络的另一个成员。 消息块可以使用筛选器函数来拒绝不想接收的消息。 本主题后面的 [消息筛选](#filtering)部分将更详细地介绍筛选器。 推迟消息的消息块可以保留该消息并在以后使用。 本主题后面的 [消息保留](#reservation)部分将对消息保留进行更详细的介绍。

代理库允许消息块异步或同步传递消息。 例如，通过使用函数将消息同步传递到消息块时， `send` 运行时会阻止当前上下文，直至目标块接受或拒绝该消息。 例如，通过使用函数将消息异步传递到消息块时， `asend` 运行时将向目标提供消息，并且如果目标接受消息，则运行时将计划将消息传播到接收方的异步任务。 运行时使用轻量级任务以协作的方式传播消息。 有关轻量级任务的详细信息，请参阅 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

应用程序将源和目标连接在一起以形成消息传递网络。 通常情况下，链接网络并调用 `send` 或 `asend` 将数据传递到网络。 若要将源消息块连接到目标，请调用 [concurrency：： ISource：： link_target](reference/isource-class.md#link_target) 方法。 若要断开源块与目标的连接，请调用 [concurrency：： ISource：： unlink_target](reference/isource-class.md#unlink_target) 方法。 若要断开源块与其所有目标的连接，请调用 [concurrency：： ISource：： unlink_targets](reference/isource-class.md#unlink_targets) 方法。 当预定义的消息块类型之一离开范围或被销毁时，它会自动将其与任何目标块断开连接。 某些消息块类型限制它们可以写入的目标的最大数目。 以下部分介绍了适用于预定义消息块类型的限制。

[[顶部](#top)]

## <a name="overview-of-message-block-types"></a><a name="overview"></a> 消息块类型概述

下表简要介绍了重要的消息块类型的角色。

[unbounded_buffer](#unbounded_buffer)<br/>
存储消息队列。

[overwrite_buffer](#overwrite_buffer)<br/>
存储一条消息，该消息可以写入和读取多次。

[single_assignment](#single_assignment)<br/>
存储一条消息，该消息可写入一次，并可从多个时间读取。

[call](#call)<br/>
在收到消息时执行工作。

[转换器](#transformer)<br/>
在接收数据时执行工作，并将该工作的结果发送给另一个目标块。 `transformer`类可以对不同的输入和输出类型进行操作。

[choice](#choice)<br/>
从一组源中选择第一个可用消息。

[联接和 multitype 联接](#join)<br/>
等待从一组源接收所有消息，然后将消息合并为另一个消息块的消息。

[记](#timer)<br/>
按固定间隔将消息发送到目标块。

这些消息块类型具有不同的特性，这些特性使它们对于不同的情况非常有用。 以下是一些特征：

- *传播类型*：消息块是用作数据源、数据接收方还是同时充当这两者。

- *消息顺序*：消息块是否维持发送或接收消息的原始顺序。 每个预定义的消息块类型保持其发送或接收消息的原始顺序。

- *源计数*：消息块可以读取的源的最大数目。

- *目标计数*：消息块可以写入的目标的最大数目。

下表显示了这些特征与各种消息块类型的关系。

|消息块类型|传播类型 (源、目标或两者) |排序或未排序 (的消息顺序) |源计数|目标计数|
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|
|`unbounded_buffer`|推送、请求和匿名|已订购|不受限制|不受限制|
|`overwrite_buffer`|推送、请求和匿名|已订购|不受限制|不受限制|
|`single_assignment`|推送、请求和匿名|已订购|不受限制|不受限制|
|`call`|目标|已订购|不受限制|不适用|
|`transformer`|推送、请求和匿名|已订购|不受限制|1|
|`choice`|推送、请求和匿名|已订购|10|1|
|`join`|推送、请求和匿名|已订购|不受限制|1|
|`multitype_join`|推送、请求和匿名|已订购|10|1|
|`timer`|Source|不适用|不适用|1|

以下各节更详细地描述了消息块类型。

[[顶部](#top)]

## <a name="unbounded_buffer-class"></a><a name="unbounded_buffer"></a> unbounded_buffer 类

[Concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)类表示常规用途的异步消息结构。 此类存储先进先出 (FIFO) 消息队列，此消息队列可由多个源写入或从多个目标读取。 当目标接收来自对象的消息时 `unbounded_buffer` ，将从消息队列中删除该消息。 因此，尽管一个 `unbounded_buffer` 对象可以具有多个目标，但只有一个目标会接收每条消息。 需将多条消息传递给另一个组件，且该组件必须接收每条消息时，`unbounded_buffer` 类十分有用。

### <a name="example"></a>示例

下面的示例演示如何使用类的基本结构 `unbounded_buffer` 。 此示例将三个值发送到一个 `unbounded_buffer` 对象，然后从同一对象中读取这些值。

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

该示例产生下面的输出：

```Output
334455
```

有关演示如何使用类的完整示例 `unbounded_buffer` ，请参阅 [如何：实现各种 Producer-Consumer 模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)。

[[顶部](#top)]

## <a name="overwrite_buffer-class"></a><a name="overwrite_buffer"></a> overwrite_buffer 类

[Concurrency：： overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)类与类相似 `unbounded_buffer` ，不同之处在于 `overwrite_buffer` 对象只存储一条消息。 此外，当目标接收来自对象的消息时 `overwrite_buffer` ，不会从缓冲区中删除该消息。 因此，多个目标将接收到该消息的副本。

`overwrite_buffer`如果要将多条消息传递给另一个组件，但该组件只需要最新的值，则类很有用。 需向多个组件广播消息时，此类也很有用。

### <a name="example"></a>示例

下面的示例演示如何使用类的基本结构 `overwrite_buffer` 。 此示例将三个值发送到一个 `overwrite _buffer` 对象，然后从同一对象中读取当前值三次。 此示例类似于类的示例 `unbounded_buffer` 。 但是， `overwrite_buffer` 类只存储一条消息。 此外，在读取对象后，运行时不会从该对象中删除该消息 `overwrite_buffer` 。

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

该示例产生下面的输出：

```Output
555555
```

有关演示如何使用类的完整示例 `overwrite_buffer` ，请参阅 [如何：实现各种 Producer-Consumer 模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)。

[[顶部](#top)]

## <a name="single_assignment-class"></a><a name="single_assignment"></a> single_assignment 类

[Concurrency：： single_assignment](../../parallel/concrt/reference/single-assignment-class.md)类与类相似 `overwrite_buffer` ，不同之处在于 `single_assignment` 对象只能写入一次。 与 `overwrite_buffer` 类相似，在目标收到来自 `single_assignment` 对象的消息时，不会从该目标删除此消息。 因此，多个目标将接收到该消息的副本。 `single_assignment`如果要将一条消息广播给多个组件，类会很有用。

### <a name="example"></a>示例

下面的示例演示如何使用类的基本结构 `single_assignment` 。 此示例将三个值发送到一个 `single_assignment` 对象，然后从同一对象中读取当前值三次。 此示例类似于类的示例 `overwrite_buffer` 。 尽管 `overwrite_buffer` 和 `single_assignment` 类存储一条消息，但该类只能 `single_assignment` 写入一次。

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

该示例产生下面的输出：

```Output
333333
```

有关演示如何使用类的完整示例 `single_assignment` ，请参阅 [演练：实现先期备货](../../parallel/concrt/walkthrough-implementing-futures.md)。

[[顶部](#top)]

## <a name="call-class"></a><a name="call"></a> call 类

[Concurrency：： call](../../parallel/concrt/reference/call-class.md)类充当接收数据时执行工作函数的消息接收方。 此工作函数可以是 lambda 表达式、函数对象或函数指针。 `call`对象的行为与普通函数调用的行为不同，因为它会并行作用于向其发送消息的其他组件。 如果 `call` 对象在收到消息时正在执行工作，则会将该消息添加到队列中。 每个 `call` 对象都按接收排队消息的顺序处理它们。

### <a name="example"></a>示例

下面的示例演示如何使用类的基本结构 `call` 。 此示例创建一个 `call` 对象，该对象将其收到的每个值输出到控制台。 然后，该示例将三个值发送给 `call` 对象。 由于 `call` 对象在单独的线程上处理消息，此示例还使用计数器变量和 [事件](../../parallel/concrt/reference/event-class.md) 对象来确保 `call` 对象在函数返回前处理所有消息 `wmain` 。

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

该示例产生下面的输出：

```Output
334455
```

有关演示如何使用类的完整示例 `call` ，请参阅 [如何：向调用和转换器类提供工作函数](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)。

[[顶部](#top)]

## <a name="transformer-class"></a><a name="transformer"></a> 变压器类

[Concurrency：：变压器](../../parallel/concrt/reference/transformer-class.md)类作为消息接收方和作为消息发送方。 `transformer`类类似于 `call` 类，因为它在接收数据时执行用户定义的工作函数。 但是， `transformer` 类还会将工作函数的结果发送给接收方对象。 与 `call` 对象一样， `transformer` 对象将并行作用于向其发送消息的其他组件。 如果 `transformer` 对象在收到消息时正在执行工作，则会将该消息添加到队列中。 每个 `transformer` 对象都按接收的顺序处理其排队的消息。

`transformer`类向一个目标发送消息。 如果在 `_PTarget` 构造函数中将参数设置为 `NULL` ，则稍后可以通过调用 [concurrency：： link_target](reference/source-block-class.md#link_target) 方法来指定目标。

与代理库提供的所有其他异步消息块类型不同， `transformer` 该类可作用于不同的输入和输出类型。 这种将数据从一种类型转换为另一种类型的功能使得 `transformer` 该类成为许多并发网络中的关键组件。 此外，还可以在对象的工作函数中添加更细化的并行功能 `transformer` 。

### <a name="example"></a>示例

下面的示例演示如何使用类的基本结构 `transformer` 。 此示例将创建一个 `transformer` 对象，该对象将每个输入值乘以0.33，以便 **`int`** 生成 **`double`** 值作为输出。 然后，该示例接收来自同一对象的转换后的值 `transformer` ，并将其输出到控制台。

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

该示例产生下面的输出：

```Output
10.8914.5218.15
```

有关演示如何使用类的完整示例 `transformer` ，请参阅 [如何：在数据管道中使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。

[[顶部](#top)]

## <a name="choice-class"></a><a name="choice"></a> choice 类

[Concurrency：： choice](../../parallel/concrt/reference/choice-class.md)类从一组源中选择第一个可用消息。 `choice`类表示一种控制流机制，而不是数据流机制 (主题[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)描述数据流和控制流) 之间的差异。

`WaitForMultipleObjects`当 `bWaitAll` 参数设置为时，从选择对象读取类似于调用 Windows API 函数 `FALSE` 。 但是， `choice` 类将数据绑定到事件本身，而不是绑定到外部同步对象。

通常，将 `choice` 类与 [concurrency：： receive](reference/concurrency-namespace-functions.md#receive) 函数结合使用来驱动应用程序中的控制流。 当必须在 `choice` 具有不同类型的消息缓冲区中进行选择时，请使用类。 当必须在 `single_assignment` 具有相同类型的消息缓冲区中进行选择时，可使用类。

将源链接到对象的顺序很 `choice` 重要，因为它可以确定选择了哪一条消息。 例如，请考虑将已包含消息的多个消息缓冲区链接到对象的情况 `choice` 。 `choice`对象从其链接到的第一个源中选择消息。 链接所有源后，对象将 `choice` 保留每个源接收消息的顺序。

### <a name="example"></a>示例

下面的示例演示如何使用类的基本结构 `choice` 。 此示例使用 [concurrency：： make_choice](reference/concurrency-namespace-functions.md#make_choice) 函数来创建一个在 `choice` 三个消息块之间进行选择的对象。 然后，该示例计算各种波那契数，并将每个结果存储在不同的消息块中。 然后，该示例将根据首先完成的操作将消息输出到控制台。

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

此示例将生成以下示例输出：

```Output
fib35 received its value first. Result = 9227465
```

由于无法保证<sup>计算35个</sup> 斐波那契数的任务首先完成，此示例的输出可能会有所不同。

此示例使用 [concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) 算法并行计算波那契契数。 有关的详细信息 `parallel_invoke` ，请参阅 [并行算法](../../parallel/concrt/parallel-algorithms.md)。

有关演示如何使用类的完整示例 `choice` ，请参阅 [如何：在已完成的任务之间进行选择](../../parallel/concrt/how-to-select-among-completed-tasks.md)。

[[顶部](#top)]

## <a name="join-and-multitype_join-classes"></a><a name="join"></a> 联接和 multitype_join 类

[Concurrency：： join](../../parallel/concrt/reference/join-class.md)和[concurrency：： multitype_join](../../parallel/concrt/reference/multitype-join-class.md)类允许您等待一组源中的每个成员接收一条消息。 `join`类作用于具有常见消息类型的源对象。 `multitype_join`类对可以具有不同消息类型的源对象进行操作。

从 `join` 或对象读取 `multitype_join` 类似于 `WaitForMultipleObjects` 在将 `bWaitAll` 参数设置为时调用 Windows API 函数 `TRUE` 。 但就像对象一样 `choice` ， `join` `multitype_join` 对象使用事件机制将数据绑定到事件本身，而不是绑定到外部同步对象。

从对象读取会 `join` 生成 std：：[vector](../../standard-library/vector-class.md) 对象。 从对象读取会 `multitype_join` 生成 std：：[元组](../../standard-library/tuple-class.md) 对象。 元素在这些对象中的显示顺序与它们对应的源缓冲区链接到或对象的顺序相同 `join` `multitype_join` 。 由于将源缓冲区链接到 `join` 或对象的顺序 `multitype_join` 与生成的或对象中的元素顺序相关联，因此 `vector` `tuple` 我们建议您不要将现有源缓冲区与联接取消链接。 这样做可能会导致未指定的行为。

### <a name="greedy-versus-non-greedy-joins"></a>贪婪联接与非贪婪联接

`join`和 `multitype_join` 类支持贪婪和非贪婪联接的概念。 *贪婪联接* 接受来自其每个源的消息，因为在所有消息都可用之前，消息将变为可用。 *非贪婪联接* 在两个阶段内接收消息。 首先，非贪婪联接将等待，直到从其每个源向其提供消息。 其次，在所有源消息都可用后，非贪婪联接将尝试保留每个消息。 如果它可以保留每条消息，它将使用所有消息并将其传播到其目标。 否则，它会发布或取消消息保留，并再次等待每个源接收消息。

贪婪联接的性能优于非贪婪联接，因为它们会立即接受消息。 但是，在极少数情况下，贪婪联接可能会导致死锁。 如果有多个包含一个或多个共享源对象的联接，则使用非贪婪联接。

### <a name="example"></a>示例

下面的示例演示如何使用类的基本结构 `join` 。 此示例使用 [concurrency：： make_join](reference/concurrency-namespace-functions.md#make_join) 函数创建一个 `join` 从三个对象接收的对象 `single_assignment` 。 此示例将计算各种波那契数字，将每个结果存储在不同的 `single_assignment` 对象中，然后将该对象所包含的每个结果打印到控制台 `join` 。 此示例与类的示例类似 `choice` ，不同之处在于 `join` 类等待所有源消息块接收消息。

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

该示例产生下面的输出：

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

此示例使用 [concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) 算法并行计算波那契契数。 有关的详细信息 `parallel_invoke` ，请参阅 [并行算法](../../parallel/concrt/parallel-algorithms.md)。

有关演示如何使用类的完整示例 `join` ，请参阅 [如何：在已完成的任务](../../parallel/concrt/how-to-select-among-completed-tasks.md) 和演练中进行选择 [：使用联接防止死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。

[[顶部](#top)]

## <a name="timer-class"></a><a name="timer"></a> timer 类

Concurrency：：[timer 类](../../parallel/concrt/reference/timer-class.md) 充当消息源。 `timer`对象在指定的时间段过后向目标发送一条消息。 `timer`当必须延迟发送消息或希望定期发送消息时，此类很有用。

`timer`类只向一个目标发送消息。 如果在 `_PTarget` 构造函数中将参数设置为 `NULL` ，则稍后可以通过调用 [Concurrency：： ISource：： link_target](reference/source-block-class.md#link_target) 方法来指定目标。

`timer`对象可以是重复的或非重复的。 若要创建重复计时器，请 **`true`** `_Repeating` 在调用构造函数时传递参数。 否则，传递以 **`false`** 使 `_Repeating` 参数创建非重复计时器。 如果计时器是重复的，则在每个间隔后，它会向其目标发送相同的消息。

代理库创建 `timer` 处于非启动状态的对象。 若要启动 timer 对象，请调用 [concurrency：： timer：： start](reference/timer-class.md#start) 方法。 若要停止 `timer` 对象，请销毁对象或调用 [concurrency：： timer：： stop](reference/timer-class.md#stop) 方法。 若要暂停重复计时器，请调用 [concurrency：： timer：:p ause](reference/timer-class.md#pause) 方法。

### <a name="example"></a>示例

下面的示例演示如何使用类的基本结构 `timer` 。 该示例使用 `timer` 和 `call` 对象来报告长时间操作的进度。

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

此示例将生成以下示例输出：

```Output
Computing fib(42)..................................................result is 267914296
```

有关演示如何使用类的完整示例 `timer` ，请参阅 [如何：按固定间隔发送消息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)。

[[顶部](#top)]

## <a name="message-filtering"></a><a name="filtering"></a> 消息筛选

创建消息块对象时，可以提供 *筛选器函数* 来确定消息块是接受还是拒绝消息。 筛选器函数是一种有效的方法，可保证消息块仅接收某些值。

下面的示例演示如何创建一个 `unbounded_buffer` 对象，该对象使用筛选器函数来仅接受偶数。 `unbounded_buffer`对象拒绝奇数，因此不会将奇数传播到其目标块。

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

该示例产生下面的输出：

```Output
0 2 4 6 8
```

筛选器函数可以是 lambda 函数、函数指针或函数对象。 每个筛选器函数都采用以下形式之一。

```Output
bool (T)
bool (T const &)
```

若要消除不必要的数据复制，请在具有通过值传播的聚合类型时使用第二种形式。

消息筛选支持 *数据流* 编程模型，在该模型中，组件在接收数据时执行计算。 有关使用筛选器函数来控制消息传递网络中的数据流的示例，请参阅 [如何：使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md)、 [演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)和 [演练：创建 Image-Processing 网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

[[顶部](#top)]

## <a name="message-reservation"></a><a name="reservation"></a> 消息保留

*消息保留* 使消息块可以保留消息供以后使用。 通常不会直接使用消息保留。 但是，了解消息保留有助于更好地了解某些预定义的消息块类型的行为。

请考虑非贪婪和贪婪联接。 这两种方法都使用消息保留来保留消息供以后使用。 如上所述，非贪婪联接在两个阶段中接收消息。 在第一阶段中，非贪婪 `join` 对象会等待其每个源接收一条消息。 然后，非贪婪联接将尝试保留每个消息。 如果它可以保留每条消息，它将使用所有消息并将其传播到其目标。 否则，它会发布或取消消息保留，并再次等待每个源接收消息。

贪婪联接也从多个源读取输入消息，使用消息保留来读取其他消息，同时等待接收来自每个源的消息。 例如，假设有一个从消息块和接收消息的贪婪 `A` 联接 `B` 。 如果贪婪联接从 B 收到两条消息，但尚未收到来自的消息 `A` ，则贪婪联接将为中的第二条消息保存唯一的消息标识符 `B` 。 在贪婪联接接收来自的消息 `A` 并将其传播到这些消息后，它将使用保存的消息标识符来查看的第二条消息是否 `B` 仍然可用。

实现自己的自定义消息块类型时，可以使用消息保留。 有关如何创建自定义消息块类型的示例，请参阅 [演练：创建自定义消息块](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)。

[[顶部](#top)]

## <a name="see-also"></a>请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)
