---
title: "“prefix”是一个 XML 前缀，不能用作表达式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30114"
  - "vbc30114"
helpviewer_keywords: 
  - "BC30114"
ms.assetid: 5cb7c89e-c61b-483a-9369-5285b7cbcf45
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “prefix”是一个 XML 前缀，不能用作表达式
“prefix”是一个 XML 前缀，不能用作表达式。 使用 GetXmlNamespace 运算符创建命名空间对象。  
  
 使用 `Imports` 语句导入的 XML 命名空间的前缀不能在 XML 文本以外使用。  
  
 **错误 ID：**BC30114  
  
### 更正此错误  
  
-   如果必须引用 XML 命名空间的一部分，请使用 `GetXmlNamespace` 运算符检索 <xref:System.Xml.Linq.XNamespace> 对象。 使用该对象取代 XML 命名空间前缀。  
  
-   如果使用 XML 命名空间前缀来限定 XML 文本，请确保对 XML 文本使用适当的语法。  
  
## 请参阅  
 [XML 文本](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [Imports 语句（XML 命名空间）](../Topic/Imports%20Statement%20\(XML%20Namespace\).md)   
 [GetXmlNamespace 运算符](../Topic/GetXmlNamespace%20Operator%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)   
 [Visual Basic 中的 LINQ 简介](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)