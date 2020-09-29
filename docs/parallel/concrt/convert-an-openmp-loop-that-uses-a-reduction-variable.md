---
title: 如何：将使用缩减变量的 OpenMP 循环转换为使用并发运行时
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: 06418bc1a331a5c77653087434a5cc621f92e7d7
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498545"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>如何：将使用缩减变量的 OpenMP 循环转换为使用并发运行时

此示例演示如何转换使用[缩减](../openmp/reference/openmp-clauses.md#reduction)子句的 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp)循环以使用并发运行时。

OpenMP `reduction` 子句使你可以指定一个或多个线程专用变量，这些变量在并行区域结束时受到缩减运算。 OpenMP 预定义一组缩减运算符。 每个缩减变量都必须是标量 (例如， **`int`** 、 **`long`** 和 **`float`**) 。 OpenMP 还定义了一些限制如何在并行区域中使用缩减变量的限制。

并行模式库 (PPL) 提供 [concurrency：：可组合](../../parallel/concrt/reference/combinable-class.md) 类，它提供可重用的线程本地存储，使你可以执行细化计算，然后将这些计算合并为最终结果。 `combinable`类是对标量和复杂类型都起作用的模板。 若要使用 `combinable` 类，请在并行构造的主体中执行子计算，然后调用 [concurrency：：可组合：：组合](reference/combinable-class.md#combine) 或 [concurrency：：可组合：： combine_each](reference/combinable-class.md#combine_each) 方法以生成最终结果。 `combine`和 `combine_each` 方法都采用*组合函数*，该函数指定如何组合每对元素。 因此， `combinable` 类并不限于一组固定的缩减运算符。

## <a name="example"></a>示例

此示例使用 OpenMP 和并发运行时来计算前35波那契数之和。

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

本示例生成以下输出。

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

有关类的详细信息 `combinable` ，请参阅 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为的文件中， `concrt-omp-fibonacci-reduction.cpp` 然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl.exe/EHsc/openmp concrt-omp-fibonacci-reduction**

## <a name="see-also"></a>请参阅

[从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)
