---
title: "运算符“&lt;operator&gt;”必须具有另一个类型为“Integer”的参数。 | Microsoft Docs"
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
  - "BC33041"
  - "vbc33041"
helpviewer_keywords: 
  - "BC33041"
ms.assetid: 5cd56f6d-2f0f-49de-a8e6-59bdb57bdb1d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 运算符“&lt;operator&gt;”必须具有另一个类型为“Integer”的参数。
使用了另一个非 `Integer` 类型的参数声明移位运算符。  
  
 在表达式中使用右移 \(`>>`\) 或左移 \(`<<`\) 运算符时，将在第二个操作数中指定位移量。 对于此操作数，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 允许你提供任何可扩展为 `Integer` 的数据类型。 但是，第二个操作数的定义被严格限制为 `Integer`。 如果将某个类或结构定义为上面带有移位运算符，则定义必须为第二个操作数指定 `Integer`。  
  
 **错误 ID：**BC33041  
  
### 更正此错误  
  
-   将移位运算符的定义更改为返回 `Integer` 值。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [移位运算符](../Topic/Bit%20Shift%20Operators%20\(Visual%20Basic\).md)