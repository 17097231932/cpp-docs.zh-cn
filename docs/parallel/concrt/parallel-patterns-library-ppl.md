---
description: '了解详细信息：并行模式库 (PPL) '
title: 并行模式库 (PPL)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library (PPL)
ms.assetid: 40fd86b2-69fa-45e5-93d8-98a75636c242
ms.openlocfilehash: ea5719e8ebaacf8f181678ef7af8aae9c900fbe6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172344"
---
# <a name="parallel-patterns-library-ppl"></a>并行模式库 (PPL)

并行模式库 (PPL) 提供命令式编程模型，以促进开发并发应用程序的可扩展性和易用性。 PPL 构建在并发运行时的计划和资源管理组件上。 通过提供并行作用于数据的泛型安全算法和容器，提高应用程序代码与基础线程机制之间的抽象级别。 使用 PPL 还可以开发通过为共享状态提供替代方案实现缩放的应用程序。

PPL 提供以下功能：

- *任务并行度*：一种机制，该机制在 Windows 线程池之上运行多个工作项 (任务并行) 

- *并行算法*：在并发运行时上工作以并行处理数据集合的泛型算法

- *并行容器和对象*：提供对其元素的安全并发访问的泛型容器类型

## <a name="example"></a>示例

PPL 提供类似于 c + + 标准库的编程模型。 下面的示例展示 PPL 的多种功能。 串行和并行计算若干 Fibonacci 数字。 两个计算都作用于 [std：： array](../../standard-library/array-class-stl.md) 对象。 示例还控制台输出了进行两种计算所需的时间。

序列版本使用 c + + 标准库 [std：： for_each](../../standard-library/algorithm-functions.md#for_each) 算法遍历数组，并将结果存储在 [std：： vector](../../standard-library/vector-class.md) 对象中。 并行版本执行相同的任务，但使用 PPL [concurrency：:p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) 算法，并将结果存储在 [concurrency：： concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 对象中。 `concurrent_vector` 类可以使每个循环迭代并发添加元素，而无需同步对容器的写访问。

由于 `parallel_for_each` 并发操作，因此本示例的并行版本必须排列 `concurrent_vector` 对象的顺序才能生成与串行版本相同的结果。

请注意，该示例使用一种简单的方法来计算波那契契数;但是，此方法说明了并发运行时如何提高长计算的性能。

[!code-cpp[concrt-parallel-fibonacci#1](../../parallel/concrt/codesnippet/cpp/parallel-patterns-library-ppl_1.cpp)]

以下是具有四个处理器的计算机的输出示例。

```Output
serial time: 9250 ms
parallel time: 5726 ms

fib(24): 46368
fib(26): 121393
fib(41): 165580141
fib(42): 267914296
```

完成每个循环迭代所需的时间各不相同。 `parallel_for_each` 的性能由最后完成的操作决定。 因此，本示例的串行版本与并行版本不会有线性的性能提高。

## <a name="related-topics"></a>相关主题

|Title|描述|
|-----------|-----------------|
|[任务并行度](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|描述 PPL 中任务和任务组的角色。|
|[并行算法](../../parallel/concrt/parallel-algorithms.md)|描述如何使用并行算法，如 `parallel_for` 和 `parallel_for_each`。|
|[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)|描述 PPL 提供的各种并行容器和对象。|
|[PPL 中的取消操作](cancellation-in-the-ppl.md)|说明如何取消并行算法当前正在执行的工作。|
|[并发运行时](../../parallel/concrt/concurrency-runtime.md)|描述可以简化并发编程并包含相关主题链接的并发运行时。|
