---
title: "运算符必须声明为“Public” | Microsoft Docs"
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
  - "vbc33011"
  - "bc33011"
helpviewer_keywords: 
  - "BC33011"
ms.assetid: 67fc0dee-4ef5-4afc-a63a-f7d20bce7954
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 运算符必须声明为“Public”
[Operator 语句](../Topic/Operator%20Statement.md) 不包括 [Public](../Topic/Public%20\(Visual%20Basic\).md) 关键字。  
  
 `Operator` 过程要求 `Public` 和 [Shared](../Topic/Shared%20\(Visual%20Basic\).md) 两个关键字，而转换运算符还要求 [Widening](../Topic/Widening%20\(Visual%20Basic\).md) 或 [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md) 关键字。  
  
 **错误 ID：**BC33011  
  
### 更正此错误  
  
-   将 `Public` 关键字添加到 `Operator` 语句中。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)