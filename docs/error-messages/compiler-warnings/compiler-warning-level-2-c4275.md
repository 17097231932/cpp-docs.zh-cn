---
description: 详细了解：编译器警告 (等级 2) C4275
title: 编译器警告（等级 2）C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: 0dd212d7439b73c28a5426574b72ff8150abe93c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173644"
---
# <a name="compiler-warning-level-2-c4275"></a>编译器警告（等级 2）C4275

> 非 DLL 接口类 "*class_1*" 用作 DLL 接口类 "*class_2*" 的基

导出的类派生自未导出的类。

若要最大程度地降低数据损坏的可能性，在使用 [__declspec (dllexport) ](../../cpp/dllexport-dllimport.md)导出类时，请确保：

- 所有静态数据都可以通过从 DLL 导出的函数进行访问。

- 类的任何内联方法都不能修改静态数据。

- 类的任何内联方法都不使用 CRT 函数或其他使用静态数据的库函数。

- 任何内联类函数都不使用 CRT 函数或其他可访问静态数据的库函数。

- 类的任何方法都不 (不管内联) 可以使用 EXE 和 DLL 中的实例化具有静态数据差异的类型。

可以通过定义用于定义具有虚函数的类的 DLL，以及可以调用来实例化和删除类型的对象的函数，来避免导出类。  然后，就可以对类型调用虚函数。

如果从 c + + 标准库中的类型派生，编译调试版本 (**/MTd**) 以及编译器错误消息所引用的位置，则可在 Visual C++ 中忽略 C4275 `_Container_base` 。

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```
