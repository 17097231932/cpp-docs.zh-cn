---
title: "此一元运算符的参数类型必须属于包含类型“&lt;typename&gt;” | Microsoft Docs"
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
  - "vbc33020"
  - "bc33020"
helpviewer_keywords: 
  - "BC33020"
ms.assetid: 9c2c2c5b-6f18-49d2-bd6e-e735a6bced77
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 此一元运算符的参数类型必须属于包含类型“&lt;typename&gt;”
一元运算符的定义使用除了在其中定义了此运算符的类或结构之外的类型来指定参数。  
  
 当你在类或结构中定义运算符时，至少一个参数应为此类或结构的类型。 对于一元运算符，唯一的操作数必须属于该类或结构的类型。  
  
 **错误 ID：**BC33020  
  
### 更正此错误  
  
-   将参数类型更改为在其中定义了运算符的类或结构的类型。  
  
-   如果要采用一种数据类型作为参数并返回不同数据类型作为运算的结果，请改为定义转换运算符。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)