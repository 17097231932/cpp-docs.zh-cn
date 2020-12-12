---
description: '了解详细信息：如何：在 c + +/CLI (用内部指针和本机指针重载函数) '
title: 如何：用内部指针和本机指针重载函数 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- Functions with interior and native pointers, overloading
ms.assetid: d70df625-4aad-457c-84f5-70a0a290cc1f
ms.openlocfilehash: f68861b7140ed3ae7fac84bc9a197f68ddd9b72d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119143"
---
# <a name="how-to-overload-functions-with-interior-pointers-and-native-pointers-ccli"></a>如何：用内部指针和本机指针重载函数 (C++/CLI)

可以重载函数，具体视参数类型是内部指针，还是本机指针而定。

> [!IMPORTANT]
> `/clr` 编译器选项支持此语言功能，但是 `/ZW` 编译器选项不支持此语言功能。

## <a name="example"></a>示例

### <a name="code"></a>代码

```cpp
// interior_ptr_overload.cpp
// compile with: /clr
using namespace System;

// C++ class
struct S {
   int i;
};

// managed class
ref struct G {
   int i;
};

// can update unmanaged storage
void f( int* pi ) {
   *pi = 10;
   Console::WriteLine("in f( int* pi )");
}

// can update managed storage
void f( interior_ptr<int> pi ) {
   *pi = 10;
   Console::WriteLine("in f( interior_ptr<int> pi )");
}

int main() {
   S *pS = new S;   // C++ heap
   G ^pG = gcnew G;   // common language runtime heap
   f( &pS->i );
   f( &pG->i );
};
```

```Output
in f( int* pi )
in f( interior_ptr<int> pi )
```

## <a name="see-also"></a>请参阅

[interior_ptr (c + +/CLI) ](interior-ptr-cpp-cli.md)
