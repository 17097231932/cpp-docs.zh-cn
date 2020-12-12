---
description: 了解详细信息： &lt; 包括&gt;
title: '&lt;包括> (c + + 文档注释) '
ms.date: 11/04/2016
f1_keywords:
- <include>
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
ms.openlocfilehash: 577281b293fcca9b9b0b9491dd239240d435f32c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199774"
---
# <a name="ltincludegt"></a>&lt;include&gt;

通过 \<include> 标记，可在其他文件中引用描述源代码中类型和成员的注释。 这是对直接在源代码文件中放入文档注释的替代方法。  例如，可以使用插入在 \<include> 整个团队或公司中使用的标准 "样板" 注释。

## <a name="syntax"></a>语法

```
<include file='filename' path='tagpath' />
```

#### <a name="parameters"></a>parameters

*filename*<br/>
包含文档的文件的名称。 可使用路径来限定文件名。  将名称括在单引号或双引号中。  如果编译器没有找到 `filename`，它会发出警告。

*tagpath*<br/>
有效 XPath 表达式，它选择文件中包含的所需节点集。

name<br/>
标记中的名称说明符（位于注释之前）；`name` 将有 `id`。

*id*<br/>
标记的 ID（位于注释之前）。  将名称括在单引号或双引号中。

## <a name="remarks"></a>备注

\<include> 标记使用 XML XPath 语法。 有关使用进行自定义的方法，请参阅 XPath 文档 \<include> 。

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 进行编译，将文档注释处理到文件中。

## <a name="example"></a>示例

这是多文件示例。 第一个使用的文件 \<include> 包含以下文档注释：

```cpp
// xml_include_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_include_tag.dll

/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test"]/*' />
public ref class Test {
   void TestMethod() {
   }
};

/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test2"]/*' />
public ref class Test2 {
   void Test() {
   }
};
```

第二个文件是 xml_include_tag.doc，包含下列文档注释：

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a>程序输出

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>t2</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a>请参阅

[XML 文档](xml-documentation-visual-cpp.md)
