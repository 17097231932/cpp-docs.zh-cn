---
description: 了解详细信息： F。版本2.0 中的新功能和说明
title: F. 版本 2.0 中的新功能和说明
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 77a27ed6d15986f787297b37a904d4625d649ced
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342460"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. 版本 2.0 中的新功能和说明

本附录汇总了从版本1.0 到版本2.0 的 OpenMP C/c + + 规范中所做的关键更改。 以下项是添加到规范中的新功能：

- OpenMP [指令](2-directives.md#21-directive-format)中允许使用逗号。

- 添加 `num_threads` 子句。 此子句允许用户请求特定数量的线程进行 [并行构造](2-directives.md#23-parallel-construct)。

- [Threadprivate](2-directives.md#271-threadprivate-directive)指令已扩展为接受静态块范围变量。

- C99 可变长度数组是完整的类型，可以在允许的任何位置指定完整的类型，如、和子句的列表中 `private` `firstprivate` `lastprivate` (参阅 [2.7.2) 部分](2-directives.md#272-data-sharing-attribute-clauses) 。

- 并行区域中的私有变量可以在嵌套指令中再次标记为 [私有](2-directives.md#2721-private) 。

- 已 `copyprivate` 添加子句。 它提供一种机制，用于使用私有变量将值从一个团队的一个成员广播到其他成员。 在提供此类共享变量时，使用共享变量作为值的一种替代方法 (例如，在递归中，需要在每个级别) 使用不同的变量。 [Copyprivate](2-directives.md#2728-copyprivate)子句只能出现在 `single` 指令上。

- 添加计时例程 [omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function) 和类似于 MPI 例程的 [omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) 。 需要这些函数才能完成墙壁时钟计时。

- 添加了一个附录，其中包含 OpenMP C/c + + 中 [实现定义的行为](e-implementation-defined-behaviors-in-openmp-c-cpp.md) 的列表。 在这些情况下，实现需要定义并记录其行为。

- 以下更改用于澄清或更正前面的适用于 C/c + + OpenMP API 规范的功能：

  - 阐明了返回非零值时 [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) 和 [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) 的行为 `omp_in_parallel` 未定义。

  - 阐明了使用嵌套并行时的 [指令嵌套](2-directives.md#29-directive-nesting) 。

  - 可以在并行区域中调用 [锁初始化](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions) 和 [锁析构](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) 函数。

  - [附录 A](a-examples.md)中添加了新示例。
