---
description: 了解详细信息： &lt; list &gt; 和 &lt; listheader&gt;
title: '&lt; (c + + 文档注释> 列表) '
ms.date: 11/04/2016
f1_keywords:
- list
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
ms.openlocfilehash: cb34e4361c68be58297d0f2e063974a2f94de991
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199202"
---
# <a name="ltlistgt-and-ltlistheadergt"></a>&lt;list &gt; 和 &lt; listheader&gt;

\<listheader> 块用于定义表或定义列表的标题行。 定义表时，只需提供标题中的术语的项。

## <a name="syntax"></a>语法

```xml
<list type="bullet" | "number" | "table">
   <listheader>
      <term>term</term>
      <description>description</description>
   </listheader>
   <item>
      <term>term</term>
      <description>description</description>
   </item>
</list>
```

#### <a name="parameters"></a>parameters

*二项式*<br/>
要定义的术语，将在 `description` 中进行定义。

description<br/>
项目符号或编号列表中的项或 `term` 的定义。

## <a name="remarks"></a>备注

列表中的每个项均使用 \<item> 块指定。 创建定义列表时，需要同时指定 `term` 和 `description`。 但是，对于表、项目符号列表或编号列表，只需提供 `description` 的项。

列表或表可根据需要具有多个 \<item> 块。

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 进行编译，将文档注释处理到文件中。

## <a name="example"></a>示例

```cpp
// xml_list_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_list_tag.dll
/// <remarks>Here is an example of a bulleted list:
/// <list type="bullet">
/// <item>
/// <description>Item 1.</description>
/// </item>
/// <item>
/// <description>Item 2.</description>
/// </item>
/// </list>
/// </remarks>
class MyClass {};
```

## <a name="see-also"></a>请参阅

[XML 文档](xml-documentation-visual-cpp.md)
