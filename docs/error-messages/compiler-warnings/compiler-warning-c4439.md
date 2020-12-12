---
description: 了解更多：编译器警告 C4439
title: 编译器警告 C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: 123f42ca495faeccc995dc1ac87572180d1dce70
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180742"
---
# <a name="compiler-warning-c4439"></a>编译器警告 C4439

"function"：签名中具有托管类型的函数定义必须具有 __clrcall 调用约定

编译器使用隐式替换调用约定 [`__clrcall`](../../cpp/clrcall.md) 。 若要解决此警告，请删除 **`__cdecl`** 或 **`__stdcall`** 调用约定。

C4439 始终作为错误发出。 可以通过或关闭此警告; 有关 `#pragma warning` **`/wd`** 详细信息，请参阅 [警告](../../preprocessor/warning.md) 或 [/w、/W0、/W1、/W2、/W3、/W4、/W1、/W2、/W3、/W4、/Wall、/wd、/we、/wo、/Wv、/wx (warning Level)](../../build/reference/compiler-option-warning-level.md) 。

## <a name="example"></a>示例

下面的示例生成 C4439。

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```
