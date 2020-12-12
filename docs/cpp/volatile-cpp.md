---
description: '了解详细信息： volatile (c + +) '
title: volatile (C++)
ms.date: 05/07/2019
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: cb7bda39ded03342b03ed889125992960210b940
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213333"
---
# <a name="volatile-c"></a>volatile (C++)

可用于声明可在程序中由硬件修改的对象的类型限定符。

## <a name="syntax"></a>语法

```
volatile declarator ;
```

## <a name="remarks"></a>备注

可以使用 [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) 编译器开关来修改编译器解释此关键字的方式。

Visual Studio 会根据 **`volatile`** 目标体系结构以不同的方式解释关键字。 对于 ARM，如果未指定 **/volatile** 编译器选项，编译器将执行，就像指定了 **/volatile： iso** 一样。 对于 ARM 之外的体系结构，如果未指定 **/volatile** 编译器选项，编译器将执行，就像指定了 **/volatile： ms** 一样;因此，对于 ARM 之外的体系结构，我们强烈建议你在处理跨线程共享的内存时指定 **/volatile： iso**，并使用显式同步基元和编译器内部函数。

您可以使用该 **`volatile`** 限定符提供对异步进程（如中断处理程序）所使用的内存位置的访问。

**`volatile`** 对还具有 [__restrict](../cpp/extension-restrict.md)关键字的变量使用时， **`volatile`** 优先使用。

如果 **`struct`** 成员标记为 **`volatile`** ，则 **`volatile`** 将传播到整个结构。 如果结构没有可通过使用一条指令在当前体系结构上复制的长度，则 **`volatile`** 在该结构上可能会完全丢失。

**`volatile`** 如果满足以下条件之一，则关键字对于字段可能不起作用：

- 可变字段的长度超过可使用一条指令在当前体系结构上复制的最大大小。

- 包含的最外面的长度 **`struct`** （如果它是可能嵌套的成员 **`struct`** ）超过了可通过使用一条指令在当前体系结构上复制的最大大小。

尽管处理器不会重新排列无法缓存的内存访问，但必须将不可缓存的变量标记为 **`volatile`** 以保证编译器不会对内存访问重新排序。

声明为的对象 **`volatile`** 不会在某些优化中使用，因为它们的值随时可能会更改。  系统总是在请求可变对象时读取该对象的当前值，即使前面的指令要求使用同一对象中的值也是如此。  此外，将在赋值时立即写入对象的值。

## <a name="iso-compliant"></a>符合 ISO

如果你熟悉 c # volatile 关键字，或熟悉 **`volatile`** 早期版本的 Microsoft c + + 编译器 (MSVC) 的行为，请注意， **`volatile`** 当指定 [/volatile： ISO](../build/reference/volatile-volatile-keyword-interpretation.md) 编译器选项时，c + + 11 ISO 标准关键字是不同的，并且在 MSVC 中受支持。 （对于 ARM，默认情况下将指定它。） **`volatile`** C + + 11 ISO 标准代码中的关键字仅用于硬件访问; 不用于线程间通信。 对于线程间的通信，请使用[c + + 标准库](../standard-library/cpp-standard-library-reference.md)中的[std：：原子 \<T> ](../standard-library/atomic.md)这样的机制。

## <a name="end-of-iso-compliant"></a>符合 ISO 的末尾

**Microsoft 专用**

使用 **/volatile： ms** 编译器选项时，默认情况下，如果目标为除 ARM 之外的体系结构，则除了维护对其他全局对象的引用，编译器还会生成额外的代码来维护对可变对象的引用。 具体而言：

- 对可变对象进行写入（也称为可变编写）具有“发布”语义；也就是说，对指令序列中的可变对象进行写入之前发生的全局或静态对象的引用将在已编译的库中写入可变对象之前发生。

- 对可变对象进行读取（也称为可变读取）具有“获取”语义；也就是说，对指令序列中的可变对象进行读取之前发生的全局或静态对象的引用将在已编译的库中读取可变对象之前发生。

这使得可在多线程应用程序中使用可变对象进行内存锁和释放。

> [!NOTE]
> 当它依赖于使用 **/volatile： ms** 编译器选项时提供的增强保证时，代码是不可移植的。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[const 和 volatile 指针](../cpp/const-and-volatile-pointers.md)
