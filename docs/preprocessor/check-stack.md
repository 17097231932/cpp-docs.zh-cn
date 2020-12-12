---
description: 了解详细信息： check_stack 杂注
title: check_stack 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
ms.openlocfilehash: 55a639e22ded788bd731aad83eb7918e1006ae4c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300848"
---
# <a name="check_stack-pragma"></a>check_stack 杂注

指示编译器在指定 **off** (或) 时关闭堆栈探测 **-** ，或 **在** 指定 (或) 时打开堆栈探测 **+** 。

## <a name="syntax"></a>语法

> **#pragma check_stack (** [{ **on**  |  **off** }] **)**\
> **#pragma check_stack** { **+**  |  **-** }

## <a name="remarks"></a>备注

此杂注出现后，当定义了第一个函数时，它就会生效。 堆栈探测既不是宏的一部分也不是以内联方式生成的函数的一部分。

如果没有为 **check_stack** 杂注提供参数，堆栈检查将还原为在命令行上指定的行为。 有关详细信息，请参阅[编译器选项](../build/reference/compiler-options.md)。 `#pragma check_stack`下表总结了和[/gs](../build/reference/gs-control-stack-checking-calls.md)选项的交互。

### <a name="using-the-check_stack-pragma"></a>使用 check_stack 杂注

|语法|是否使用<br /><br /> /Gs 选项进行编译？|操作|
|------------|------------------------------------|------------|
|`#pragma check_stack( )` 或<br /><br /> `#pragma check_stack`|是|为后面的函数关闭堆栈检查|
|`#pragma check_stack( )` 或<br /><br /> `#pragma check_stack`|否|为后面的函数打开堆栈检查|
|`#pragma check_stack(on)`<br /><br /> 或 `#pragma check_stack +`|是或否|为后面的函数打开堆栈检查|
|`#pragma check_stack(off)`<br /><br /> 或 `#pragma check_stack -`|是或否|为后面的函数关闭堆栈检查|

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
