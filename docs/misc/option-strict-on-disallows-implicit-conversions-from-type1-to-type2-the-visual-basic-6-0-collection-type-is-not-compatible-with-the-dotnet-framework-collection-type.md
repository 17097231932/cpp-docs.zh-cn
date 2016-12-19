---
title: "Option Strict On 不允许从“&lt;type1&gt;”到“&lt;type2&gt;”的隐式转换；Visual Basic 6.0 集合类型与 .NET Framework 集合类型不兼容 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30753"
  - "bc30753"
helpviewer_keywords: 
  - "BC30753"
ms.assetid: 7e1bb22e-a507-483e-bfd6-f3a43e24a232
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On 不允许从“&lt;type1&gt;”到“&lt;type2&gt;”的隐式转换；Visual Basic 6.0 集合类型与 .NET Framework 集合类型不兼容
`Option Strict On` 不允许从“`<type1>`”到“`<type2>`”的隐式转换；Visual Basic 6.0 集合类型与 [!INCLUDE[dnprdnshort](../Token/dnprdnshort_md.md)] 集合类型不兼容。  
  
 Visual Basic 6.0 中使用的集合对象与 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 中使用的集合对象不同。  
  
 **错误 ID：**BC30753  
  
### 更正此错误  
  
-   使用一个类型转换关键字显式转换集合对象。 如果转换失败，[CType 函数](../Topic/CType%20Function%20\(Visual%20Basic\).md) 和 [DirectCast 运算符](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md) 关键字会引发运行时异常。 如果转换失败，[TryCast 运算符](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md) 关键字会返回 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)。  
  
## 请参阅  
 [CType 函数](../Topic/CType%20Function%20\(Visual%20Basic\).md)   
 [DirectCast 运算符](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md)   
 [TryCast 运算符](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md)   
 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)   
 [NIB Visual Basic 中的集合](http://msdn.microsoft.com/zh-cn/8b2b7845-2251-4573-8dd3-c9f9c0a66a21)