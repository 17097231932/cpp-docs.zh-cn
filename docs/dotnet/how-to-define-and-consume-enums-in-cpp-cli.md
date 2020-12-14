---
description: 了解有关详细信息，请参阅如何：在 c + +/CLI 中定义和使用枚举
title: 如何：在 C++/CLI 中定义和使用枚举
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: 26b3c886ca34235f0567fc0f8e9d7df6bfe46814
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258337"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>如何：在 C++/CLI 中定义和使用枚举

本主题讨论 c + +/CLI 中的枚举。

## <a name="specifying-the-underlying-type-of-an-enum"></a>指定枚举的基础类型

默认情况下，枚举的基础类型是 **`int`** 。  不过，您可以将类型指定为有符号或无符号形式的 **`int`** 、 **`short`** 、、 **`long`** **`__int32`** 或 **`__int64`** 。  你还可以使用 **`char`** 。

```cpp
// mcppv2_enum_3.cpp
// compile with: /clr
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};

int main() {
   // fully qualified names, enumerator not injected into scope
   day_char d = day_char::sun, e = day_char::mon;
   System::Console::WriteLine(d);
   char f = (char)d;
   System::Console::WriteLine(f);
   f = (char)e;
   System::Console::WriteLine(f);
   e = day_char::tue;
   f = (char)e;
   System::Console::WriteLine(f);
}
```

**输出**

```Output
sun
0
1
2
```

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>如何在托管和标准枚举之间转换

枚举和整型之间没有标准转换;需要强制转换。

```cpp
// mcppv2_enum_4.cpp
// compile with: /clr
enum class day {sun, mon, tue, wed, thu, fri, sat};
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum

int main() {
   day a = day::sun;
   day2 = sun;
   if ((int)a == day2)
   // or...
   // if (a == (day)day2)
      System::Console::WriteLine("a and day2 are the same");
   else
      System::Console::WriteLine("a and day2 are not the same");
}
```

**输出**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>运算符和枚举

以下运算符对 c + +/CLI 中的枚举有效：

|运算符|
|--------------|
|== != \< >\<= >=|
|+ -|
|&#124; ^ & ~|
|++ --|
|sizeof|

运算符 &#124; ^ & ~ + +--仅为具有整数基础类型的枚举定义，不包括 bool。  两个操作数都必须是枚举类型。

编译器不会对枚举操作的结果进行静态或动态检查;操作可能导致不在枚举的有效枚举器范围内的值。

> [!NOTE]
> C + + 11 在非托管代码中引入了与 c + +/CLI 中的托管枚举类截然不同的枚举类类型。 特别是，c + + 11 枚举类类型不支持与 c + +/CLI 中的托管枚举类类型相同的运算符，并且 c + +/CLI 源代码必须在托管枚举类声明中提供可访问性说明符，以便将它们与非托管 (c + + 11) 枚举类声明区分开来。 有关 c + +/CLI、c + +/CX 和 c + + 11 中的枚举类的详细信息，请参阅 [enum 类](../extensions/enum-class-cpp-component-extensions.md)。

```cpp
// mcppv2_enum_5.cpp
// compile with: /clr
private enum class E { a, b } e, mask;
int main() {
   if ( e & mask )   // C2451 no E->bool conversion
      ;

   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)
      ;

   if ( ( e & mask ) != E() )   // OK
      ;
}
```

```cpp
// mcppv2_enum_6.cpp
// compile with: /clr
private enum class day : int {sun, mon};
enum : bool {sun = true, mon = false} day2;

int main() {
   day a = day::sun, b = day::mon;
   day2 = sun;

   System::Console::WriteLine(sizeof(a));
   System::Console::WriteLine(sizeof(day2));
   a++;
   System::Console::WriteLine(a == b);
}
```

**输出**

```Output
4
1
True
```

## <a name="see-also"></a>请参阅

[枚举类](../extensions/enum-class-cpp-component-extensions.md)
