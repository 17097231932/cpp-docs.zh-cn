---
title: "“Widening”不能与“Narrowing”组合 | Microsoft Docs"
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
  - "bc33001"
  - "vbc33001"
helpviewer_keywords: 
  - "BC33001"
ms.assetid: 1c576344-083c-45ad-bc71-0489bd3976be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Widening”不能与“Narrowing”组合
[Operator 语句](../Topic/Operator%20Statement.md) 同时指定 [Widening](../Topic/Widening%20\(Visual%20Basic\).md) 和 [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md)。  
  
 在定义转换运算符时，必须将其声明为 `Widening` 或 `Narrowing`。 由于这些特征相互排斥，因此你不能同时指定两者。  
  
 **错误 ID：**BC33001  
  
### 更正此错误  
  
-   从 `Operator` 语句中删除 `Widening` 或 `Narrowing` 关键字。 你必须指定一个或另一个。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)