---
description: 了解详细信息： &lt; 请参阅&gt;
title: '&lt;请参阅> (c + + 文档注释) '
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: b4f8f9a2312a3db1ce2840209668b7b23837ab31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224733"
---
# <a name="ltseegt"></a>&lt;see&gt;

\<see> 标记可用于从文本内指定链接。 用于 [\<seealso>](seealso-visual-cpp.md) 指示你可能希望在 "另请参见" 部分中显示的文本。

## <a name="syntax"></a>语法

```
<see cref="member"/>
```

#### <a name="parameters"></a>parameters

*职员*<br/>
对可从当前编译环境调用的成员或字段的引用。  将名称括在单引号或双引号中。

编译器检查是否存在给定的码位元素，并将 `member` 解析为输出 XML 中的元素名称。  如果编译器没有找到 `member`，它会发出警告。

## <a name="remarks"></a>备注

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 进行编译，将文档注释处理到文件中。

有关使用 \<see> 的示例，请参阅 [\<summary>](summary-visual-cpp.md)。

MSVC 编译器将尝试通过文档注释来解析一次中的 cref 引用。  因此，如果使用 C++ 查找规则，编译器找不到符号，引用将被标记为未解析。 [\<seealso>](seealso-visual-cpp.md)有关详细信息，请参阅。

## <a name="example"></a>示例

以下示例显示了如何对泛型类型进行 cref 引用，以便编译器解析该引用。

```cpp
// xml_see_cref_example.cpp
// compile with: /LD /clr /doc
// the following cref shows how to specify the reference, such that,
// the compiler will resolve the reference
/// <see cref="C{T}">
/// </see>
ref class A {};

// the following cref shows another way to specify the reference,
// such that, the compiler will resolve the reference
/// <see cref="C < T >"/>

// the following cref shows how to hard-code the reference
/// <see cref="T:C`1">
/// </see>
ref class B {};

/// <see cref="A">
/// </see>
/// <typeparam name="T"></typeparam>
generic<class T>
ref class C {};
```

## <a name="see-also"></a>请参阅

[XML 文档](xml-documentation-visual-cpp.md)
