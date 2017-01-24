---
title: "应为关系运算符 | Microsoft Docs"
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
  - "bc30239"
  - "vbc30239"
helpviewer_keywords: 
  - "BC30239"
ms.assetid: c5701568-77a1-441b-a0f7-f7b36cbd17e3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 应为关系运算符
`Case` 语句包含 `Is` 子句，但不包含 `=` 或 `>` 等比较运算符。 如果 `Case` 语句中没有包含一个运算符，则采用 `=`，不使用 `Is`。  
  
 **错误 ID:** BC30239  
  
### 更正此错误  
  
-   删除 `Is` 关键字或在其后面添加一个比较运算符。  
  
## 请参阅  
 [Select...Case 语句](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)   
 [比较运算符 \(Visual Basic\)](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)   
 [比较运算符](../Topic/Comparison%20Operators%20\(Visual%20Basic\).md)