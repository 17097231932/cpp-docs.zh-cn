---
title: "运算符“&lt;operator&gt;”必须有一个或两个参数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33016"
  - "vbc33016"
helpviewer_keywords: 
  - "BC33016"
ms.assetid: 70f43905-037e-4040-83c0-f39334b3e07a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 运算符“&lt;operator&gt;”必须有一个或两个参数
未使用参数或使用两个以上的参数定义了可能是一元或二元的运算符。  
  
 一元\/二元运算符必须有一个或两个参数。  
  
 **错误 ID：**BC33016  
  
### 更正此错误  
  
-   调整定义以指定一个或两个参数。  
  
-   如果不需要参数或需要两个以上的参数，则必须使用 [Function 语句](../Topic/Function%20Statement%20\(Visual%20Basic\).md) 来定义 `Function` 过程（而不是运算符）。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)