---
description: 了解更多： c + + 位域
title: C++ 位域
ms.date: 11/19/2018
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: 3cf1eb3e3beb0da69a4c148a48e7c68e23804d1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344583"
---
# <a name="c-bit-fields"></a>C++ 位域

类和结构可包含比整型类型占用更少存储空间的成员。 这些成员被指定为位域。 位字段 *成员声明符* 的语法如下所示：

## <a name="syntax"></a>语法

*声明符* **：** *常量表达式*

## <a name="remarks"></a>备注

 (可选) *声明符* 是在程序中访问该成员时所依据的名称。 它必须是整型类型（包括枚举类型）。 *常数表达式* 指定成员在结构中所占用的位数。 匿名位域 — 即不带标识符的位域成员，可用于填充。

> [!NOTE]
> 宽度为0的未命名位域强制将下一个位域与下一个 **类型** 边界对齐，其中 **type** 是成员的类型。

下面的示例声明包含位域的结构：

```cpp
// bit_fields1.cpp
// compile with: /LD
struct Date {
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)
   unsigned short nMonth    : 5;    // 0..12  (5 bits)
   unsigned short nYear     : 8;    // 0..100 (8 bits)
};
```

`Date` 类型的对象的概念上的内存布局如下图所示。

![Date 对象的内存布局](../cpp/media/vc38uq1.png "Date 对象的内存布局") <br/>
数据对象的内容布局

请注意， `nYear` 长度为8位，并将溢出声明类型的字边界 **`unsigned short`** 。 因此，它从新的开头开始 **`unsigned short`** 。 并不必使所有位域均适合基础类型的对象；根据声明中请求的位数来分配新的存储单元。

**Microsoft 专用**

声明为位域的数据从低位到高位进行排序，如上图所示。

**结束 Microsoft 专用**

如果结构的声明包含长度为 0 的未命名字段（如以下示例所示），

```cpp
// bit_fields2.cpp
// compile with: /LD
struct Date {
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned nMonthDay : 6;    // 0..31  (6 bits)
   unsigned           : 0;    // Force alignment to next boundary.
   unsigned nMonth    : 5;    // 0..12  (5 bits)
   unsigned nYear     : 8;    // 0..100 (8 bits)
};
```

然后，内存布局如下图所示：

![具有零&#45;长度位域的 Date 对象的布局](../cpp/media/vc38uq2.png "具有零&#45;长度位域的 Date 对象的布局") <br/>
带有零长度位域的数据对象的布局

位域的基础类型必须是整型，如 [内置类型](../cpp/fundamental-types-cpp.md)中所述。

如果类型引用的初始值设定项 `const T&` 是引用类型的位域的左值 `T` ，则引用不会直接绑定到位域。 相反，引用绑定到一个临时初始化的，以容纳位域的值。

## <a name="restrictions-on-bit-fields"></a>位域的限制

以下列表详述了位域的错误操作：

- 采用位域的地址。

- **`const`** 使用位域初始化非引用。

## <a name="see-also"></a>请参阅

[类和结构](../cpp/classes-and-structs-cpp.md)
