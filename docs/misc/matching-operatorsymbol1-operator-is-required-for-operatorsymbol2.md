---
title: "“&lt;operatorsymbol2&gt;”需要匹配的“&lt;operatorsymbol1&gt;”运算符 | Microsoft Docs"
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
  - "bc33033"
  - "vbc33033"
helpviewer_keywords: 
  - "BC33033"
ms.assetid: d2805e4f-08a8-4760-9539-565f51b88d13
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;operatorsymbol2&gt;”需要匹配的“&lt;operatorsymbol1&gt;”运算符
在未定义所需匹配运算符的情况下定义了某个运算符。  
  
 必须将以下运算符定义为匹配对：  
  
-   `=` 和 `<>`  
  
-   `>` 和 `<`  
  
-   `>=` 和 `<=`  
  
-   `IsTrue` 和 `IsFalse`  
  
 如果在类或结构中定义以上任意运算符，你必须同时在同一个类或结构中定义它的匹配运算符。  
  
 即使没有明确地使用匹配运算符，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 也可能需要使用它。 例如，如果定义在 [For...Next 语句](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md) 中用作计数器变量的类或结构，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 将同时需要 `>=` 和 `<=` 运算符（以及 `+` 运算符）。  
  
 **错误 ID：**BC33033  
  
### 更正此错误  
  
-   在同一个类或结构中定义匹配运算符。 请尽量将它定义得有意义，因为 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 可能会在你未预计到的情况下使用它。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [运算符和表达式](../Topic/Operators%20and%20Expressions%20in%20Visual%20Basic.md)