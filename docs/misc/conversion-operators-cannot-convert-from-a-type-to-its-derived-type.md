---
title: "转换运算符不能从某类型转换为它的派生类型 | Microsoft Docs"
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
  - "vbc33027"
  - "bc33027"
helpviewer_keywords: 
  - "BC33027"
ms.assetid: 861954f2-f563-4234-af84-bdd02f39979b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 转换运算符不能从某类型转换为它的派生类型
转换运算符是用派生自参数类型的返回类型声明的。  
  
 编译时，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 会认为在其继承层次结构中存在从任何引用类型到任何类型的预定义转换，即，派生该类型的任何类型或该类型所派生的任何类型。 这种转换在运行时可能会失败，但编译器无法预知运行时结果，因此它允许编译任何这种转换。  
  
 由于编译器认为已定义此转换，因此它不允许你对其重新定义。  
  
 **错误 ID：**BC33027  
  
### 更正此错误  
  
-   完全删除此运算符定义。 已对其进行预定义。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)