---
title: "已使用接口类型将转换运算符声明为返回类型 | Microsoft Docs"
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
  - "vbc33025"
  - "bc33025"
helpviewer_keywords: 
  - "BC33025"
ms.assetid: 7e13dfa3-2b70-4ca6-a8ec-159131fd2c4c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 已使用接口类型将转换运算符声明为返回类型
通过接口类型将转换运算符声明为返回类型。  
  
 在编译时，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 认为存在一个从任何引用类型到任何接口的预定义转换。 这种转换在运行时可能会失败，但编译器无法预知运行时结果，因此它允许编译任何这种转换。  
  
 由于编译器认为已定义此转换，因此它不允许你对其重新定义。  
  
 **错误 ID：**BC33025  
  
### 更正此错误  
  
-   完全删除此运算符定义。 已对其进行预定义。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)