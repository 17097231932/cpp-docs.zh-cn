---
description: 了解详细信息：链接器工具错误 LNK1313
title: 链接器工具错误 LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: 1c10038def9a448645e80ae10fc47d4372769b58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310707"
---
# <a name="linker-tools-error-lnk1313"></a>链接器工具错误 LNK1313

> 检测到 ijw/native 模块；不能与纯模块链接

## <a name="remarks"></a>备注

Visual C++ 的当前版本不支持将本机或混合托管/本机 .obj 文件链接到用 **/clr： pure** 编译的 .obj 文件。

**/Clr： pure** 编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

## <a name="examples"></a>示例

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

下面的示例将生成 LNK1313。

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```
