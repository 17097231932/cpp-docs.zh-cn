---
description: 了解详细信息：编译器警告 (等级 1) C4772
title: 编译器警告（等级 1）C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 41fcbf3074cb1e51e06ba21a01a27eaf8ded1b31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228438"
---
# <a name="compiler-warning-level-1-c4772"></a>编译器警告（等级 1）C4772

> \#从缺少的类型库中导入引用的类型;"*缺少-type*" 用作占位符

使用 [#import](../../preprocessor/hash-import-directive-cpp.md) 指令引用了类型库。 但是，类型库包含对未引用的另一个类型库的引用 `#import` 。 编译器找不到此其他 .tlb 文件。

请注意，如果使用 [/i (其他包含目录) ](../../build/reference/i-additional-include-directories.md) 编译器选项来指定这些目录，则编译器将不会在不同的目录中找到类型库。 如果希望编译器在不同的目录中查找类型库，请将这些目录添加到 PATH 环境变量中。

默认情况下，此警告作为错误发出。 不能将 C4772 与/W0. 一起禁用

## <a name="example"></a>示例

这是再现 C4772 所需的第一个类型库。

```IDL
// c4772a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C4772aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]
   enum E_C4772a
   {
      one, two, three
   };
};
```

这是再现 C4772 所需的第二个类型库。

```IDL
// c4772b.idl
// post-build command: del /f C4772a.tlb
// C4772a.tlb is available when c4772b.tlb is built
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4772bLib
{
   importlib ("c4772a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4772b
   {
      enum E_C4772a e;
   };
};
```

下面的示例生成 C4772：

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```
