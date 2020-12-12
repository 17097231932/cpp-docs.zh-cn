---
description: '了解有关以下内容的详细信息：转换运算符： ( # A1'
title: 强制转换运算符：()
ms.date: 11/04/2016
helpviewer_keywords:
- cast operators [C++]
- () cast operator
ms.assetid: 4c99eb92-1b19-4a5d-9840-5d8c29b8453e
ms.openlocfilehash: d80336fdd9d9e73f0af17703cc09fef7a599fce1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308596"
---
# <a name="cast-operator-"></a>强制转换运算符：()

在特定情况下，类型强制转换提供了用于显式转换对象类型的方法。

## <a name="syntax"></a>语法

```
unary-expression ( type-name ) cast-expression
```

## <a name="remarks"></a>备注

任何一元表达式均会被视为强制转换表达式。

在进行类型强制转换后，编译器将 cast-expression  视为类型 type-name  。 强制转换可用于在任意标量类型的对象与任何其他标量类型之间进行来回转换。 显式类型强制转换由确定隐式转换效果的相同规则约束。 有关强制转换的其他约束可能来源于特定类型的实际大小或表示形式。

## <a name="examples"></a>示例

```cpp
// expre_CastOperator.cpp
// compile with: /EHsc
// Demonstrate cast operator
#include <iostream>

using namespace std;

int main()
{
    double x = 3.1;
    int i;
    cout << "x = " << x << endl;
    i = (int)x;   // assign i the integer part of x
    cout << "i = " << i << endl;
}
```

```cpp
// expre_CastOperator2.cpp
// The following sample shows how to define and use a cast operator.
#include <string.h>
#include <stdio.h>

class CountedAnsiString
{
public:
    // Assume source is not null terminated
    CountedAnsiString(const char *pStr, size_t nSize) :
                      m_nSize(nSize)
    {
        m_pStr = new char[sizeOfBuffer];

        strncpy_s(m_pStr, sizeOfBuffer, pStr, m_nSize);
        memset(&m_pStr[m_nSize], '!', 9); // for demonstration purposes.
    }

    // Various string-like methods...

    const char *GetRawBytes() const
    {
        return(m_pStr);
    }

    //
    // operator to cast to a const char *
    //
    operator const char *()
    {
        m_pStr[m_nSize] = '\0';
        return(m_pStr);
    }

    enum
    {
        sizeOfBuffer = 20
    } size;

private:
    char *m_pStr;
    const size_t m_nSize;
};

int main()
{
    const char *kStr = "Excitinggg";
    CountedAnsiString myStr(kStr, 8);

    const char *pRaw = myStr.GetRawBytes();
    printf_s("RawBytes truncated to 10 chars:   %.10s\n", pRaw);

    const char *pCast = myStr; // or (const char *)myStr;
    printf_s("Casted Bytes:   %s\n", pCast);

    puts("Note that the cast changed the raw internal string");
    printf_s("Raw Bytes after cast:   %s\n", pRaw);
}
```

```Output
RawBytes truncated to 10 chars:   Exciting!!
Casted Bytes:   Exciting
Note that the cast changed the raw internal string
Raw Bytes after cast:   Exciting
```

## <a name="see-also"></a>请参阅

[使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[显式类型转换运算符： ( # B1 ](../cpp/explicit-type-conversion-operator-parens.md)<br/>
[转换运算符](../cpp/casting-operators.md)<br/>
[Cast 运算符](../c-language/cast-operators.md)
