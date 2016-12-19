---
title: "“New”不能在接口上使用 | Microsoft Docs"
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
  - "vbc30375"
  - "bc30375"
helpviewer_keywords: 
  - "BC30375"
ms.assetid: c1e06108-1b52-4cbe-8cae-e816a0dbac0b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “New”不能在接口上使用
将一个变量声明为一个接口类型时，[Dim 语句](../Topic/Dim%20Statement%20\(Visual%20Basic\).md) 使用 [New 运算符](../Topic/New%20Operator%20\(Visual%20Basic\).md) 子句。  
  
 尽管接口为引用类型，你也不能创建它的实例。 你仅可使用 `New` 来创建类或结构的实例。  
  
 **错误 ID：**BC30375  
  
### 更正此错误  
  
1.  如果变量为接口类型，删除 `New` 关键字。  
  
2.  如果变量引用实例，将其声明为类或结构类型。 保留 `New` 关键字来创建实例。  
  
## 请参阅  
 [Interface 语句](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Class 语句](../Topic/Class%20Statement%20\(Visual%20Basic\).md)   
 [Structure 语句](../Topic/Structure%20Statement.md)