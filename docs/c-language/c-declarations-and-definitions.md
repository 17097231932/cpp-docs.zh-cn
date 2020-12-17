---
description: 详细了解：C 声明和定义
title: C 声明和定义
ms.date: 11/04/2016
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
ms.openlocfilehash: dac53ac203c8e58e3af87e4869983c0443ffb092
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254308"
---
# <a name="c-declarations-and-definitions"></a>C 声明和定义

“声明”在特定变量、函数或类型及其特性之间建立关联。 [声明概述](../c-language/overview-of-declarations.md)为 `declaration` 非终止符提供了 ANSI 语法。 声明还指定可访问标识符的位置和时间（标识符的“链接”）。 有关链接的信息，请参阅[生存期、可见性和链接](../c-language/lifetime-scope-visibility-and-linkage.md)。

变量的“定义”将建立与声明建立的相同的关联，但也会导致为变量分配存储。

例如，`main`、`find` 和 `count` 函数以及 `var` 和 `val` 变量在一个源文件中定义，顺序如下：

```
int main() {}

int var = 0;
double val[MAXVAL];
char find( fileptr ) {}
int count( double f ) {}
```

变量 `var` 和 `val` 可用于 `find` 和 `count` 函数中；无需进一步声明。 但是，这些名称在 `main` 中不可见（无法访问）。

## <a name="see-also"></a>请参阅

[源文件和源程序](../c-language/source-files-and-source-programs.md)
