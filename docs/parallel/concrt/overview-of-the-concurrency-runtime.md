---
description: 了解详细信息：概述并发运行时
title: 并发运行时的概述
ms.date: 11/19/2018
helpviewer_keywords:
- Concurrency Runtime, requirements
- Concurrency Runtime, architecture
- Concurrency Runtime, overview
- Concurrency Runtime, lambda expressions
ms.assetid: 56237d96-10b0-494a-9cb4-f5c5090436c5
ms.openlocfilehash: b6ff531b1961b32056a7232b62eca05d7a8793b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189153"
---
# <a name="overview-of-the-concurrency-runtime"></a>并发运行时的概述

本文档对并发运行时进行了概述。 它介绍并发运行时的优势、何时使用它、其组件如何相互交互以及与操作系统和应用程序交互。

## <a name="sections"></a><a name="top"></a> 个

本文档包含以下各节：

- [并发运行时实现历史记录](#dlls)

- [并发运行时非常重要的原因](#runtime)

- [体系结构](#architecture)

- [C++ Lambda 表达式](#lambda)

- [惠?](#requirements)

## <a name="concurrency-runtime-implementation-history"></a><a name="dlls"></a> 并发运行时实现历史记录

在 Visual Studio 2010 到2013中，并发运行时已合并到 msvcr100.dll msvcr120.dll 中。  在 Visual Studio 2015 中发生 UCRT 重构后，该 DLL 将重构为三个部分：

- 在 Windows 10 中随附的 ucrtbase.dll – C API，并通过 Windows 更新提供服务

- vcruntime140.dll –通过 Visual Studio 随附的编译器支持函数和 EH 运行时

- concrt140.dll –并发运行时，通过 Visual Studio 发运。 对于并行容器和算法（如）是必需的 `concurrency::parallel_for` 。 此外，STL 在 Windows XP 上需要此 DLL 来增强同步基元，因为 Windows XP 没有 condition 变量。

在 Visual Studio 2015 及更高版本中，并发运行时任务计划程序不再是 ppltasks.h 中的任务类和相关类型的计划程序。 这些类型现在使用 Windows 线程池来实现更好的性能以及与 Windows 同步基元之间进行互操作。

## <a name="why-a-runtime-for-concurrency-is-important"></a><a name="runtime"></a> 并发运行时的重要性

并发运行时向同时运行的应用程序和应用程序组件提供一致性和可预测性。 并发运行时的好处有两个示例： *协作任务计划* 和 *协作式阻止*。

并发运行时使用一种协作任务计划程序，该计划程序实现工作窃取算法来高效地在计算资源间分布工作。 例如，考虑具有由同一个运行时管理的两个线程的应用程序。 如果一个线程完成其计划任务，则它可以从另一个线程卸载工作。 此机制可平衡应用程序的整体工作负载。

并发运行时还提供了使用协作阻止来同步资源访问的同步基元。 例如，考虑一个必须独占访问共享资源的任务。 通过协作阻止，运行时可以在第一个任务等待资源时，使用剩余量程执行另一个任务。 此机制可提升计算资源的最大使用率。

[[顶部](#top)]

## <a name="architecture"></a><a name="architecture"></a>体系结构

并发运行时划分为四个组件：并行模式库 (PPL)、异步代理库、任务计划程序和资源管理器。 这些组件驻留在操作系统与应用程序之间。 下图显示并发运行时组件如何在操作系统和应用程序间进行交互：

**并发运行时体系结构**

![并发运行时体系结构](../../parallel/concrt/media/concurrencyrun.png "并发运行时体系结构")

> [!IMPORTANT]
> 任务计划程序和资源管理器组件不可从通用 Windows 平台 (UWP) 应用程序或使用 ppltasks.h 中的任务类或其他类型。

并发运行时是高度可 *组合* 的，也就是说，可以结合现有功能来执行更多操作。 并发运行时从较低级别组件组合了许多功能，如并行算法。

并发运行时还提供了使用协作阻止来同步资源访问的同步基元。 有关这些同步基元的详细信息，请参阅 [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)。

以下各部分提供每个组件提供了的功能以及何时使用它的简要概述。

### <a name="parallel-patterns-library"></a>并行模式库

并行模式库 (PPL) 提供通用的容器和算法，用于执行细化并行。 PPL 通过提供并行算法来实现 *命令式数据并行性* ，该算法可跨计算资源分配集合或数据集上的计算。 它还通过提供跨计算资源分发多个独立操作的任务对象来启用 *任务并行* 。

当你具有可以受益于并行执行的本地计算时，可使用并行模式库。 例如，可以使用 [concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 算法来转换现有 **`for`** 循环以并行操作。

有关并行模式库的详细信息，请参阅 [并行模式库 (PPL) ](../../parallel/concrt/parallel-patterns-library-ppl.md)。

### <a name="asynchronous-agents-library"></a>异步代理库

 (或仅) *代理库* 的异步代理库提供了基于角色的编程模型和消息传递接口，用于粗粒度数据流和管道任务。 异步代理使你可以通过在其他组件等待数据时执行工作来高效地使用延迟。

当你具有相互之间进行异步通信的多个实体时，可使用代理库。 例如，可以创建从文件或网络连接读取数据，然后使用消息传递接口将该数据发送到另一个代理的代理。

有关代理库的详细信息，请参阅 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。

### <a name="task-scheduler"></a>任务计划程序

任务计划程序在运行时计划和协调任务。 任务计划程序是协作性的，使用工作窃取算法实现处理资源的最大使用率。

并发运行时提供了默认计划程序，因此你无需管理基础结构详细信息。 但是，为了满足应用程序的质量要求，你还可以提供自己的计划策略或将特定计划程序与特定任务相关联。

有关任务计划程序的详细信息，请参阅 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

### <a name="resource-manager"></a>Resource Manager

资源管理器的作用是管理计算资源，如处理器和内存。 资源管理器可将资源分配到它们可能最有效的位置，从而在工作负载在运行时发生变化时响应它们。

资源管理器充当计算资源的抽象，主要与任务计划程序进行交互。 尽管可以使用资源管理器来微调库和应用程序的性能，但是通常会使用并行模式库、代理库和任务计划程序提供的功能。 这些库使用资源管理器在工作负载变化时动态地重新平衡资源。

[[顶部](#top)]

## <a name="c-lambda-expressions"></a><a name="lambda"></a> C + + Lambda 表达式

并发运行时定义的许多类型和算法作为 C++ 模板实现。 其中某些类型和算法采用执行工作的例程作为参数。 此参数可以是 lambda 函数、函数对象或函数指针。 这些实体也称为 *工作函数* 或 *工作例程*。

Lambda 表达式是重要的新 Visual C++ 语言功能，因为它们提供了一种为并行处理定义工作函数的简洁方法。 函数对象和函数指针使你可以将并发运行时用于现有代码。 但是，我们建议你在编写新代码时使用 lambda 表达式，因为它们可提供安全性和工作效率优势。

下面的示例将多个调用中的 lambda 函数、函数对象和函数指针的语法与 [concurrency：:p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 算法进行比较。 对的每个调用都 `parallel_for_each` 使用不同的技术来计算 [std：： array](../../standard-library/array-class-stl.md) 对象中每个元素的平方。

[!code-cpp[concrt-comparing-work-functions#1](../../parallel/concrt/codesnippet/cpp/overview-of-the-concurrency-runtime_1.cpp)]

**输出**

```Output
1
256
6561
65536
390625
```

有关 c + + 中的 lambda 函数的详细信息，请参阅 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)。

[[顶部](#top)]

## <a name="requirements"></a><a name="requirements"></a>要求

下表显示与并发运行时的每个组件关联的头文件：

|组件|标头文件|
|---------------|------------------|
|并行模式库 (PPL)|ppl.h<br /><br /> concurrent_queue.h<br /><br /> concurrent_vector.h|
|异步代理库|agents.h|
|任务计划程序|concrt.h|
|Resource Manager|concrtrm.h|

并发运行时在 [并发](../../parallel/concrt/reference/concurrency-namespace.md) 命名空间中声明。  (还可以使用 [并发性](../../parallel/concrt/reference/concurrency-namespace.md)，这是此命名空间的别名。 ) `concurrency::details` 命名空间支持并发运行时框架，不应在代码中直接使用。

并发运行时作为 C 运行时库 (CRT) 的一部分提供。 有关如何生成使用 CRT 的应用程序的详细信息，请参阅 [Crt 库功能](../../c-runtime-library/crt-library-features.md)。

[[顶部](#top)]
