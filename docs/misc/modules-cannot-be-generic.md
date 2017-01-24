---
title: "模块不能为泛型。 | Microsoft Docs"
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
  - "BC32073"
  - "vbc32073"
helpviewer_keywords: 
  - "BC32073"
ms.assetid: 47246e2b-51d4-4a10-a3ac-bc77b44fa2ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 模块不能为泛型。
`Module` 语句使用 `Of` 关键字来引入泛型类型参数。  
  
 你可以定义并使用泛型类、结构、接口、过程和委托。 不能定义泛型模块。  
  
 **错误 ID：**BC32073  
  
### 更正此错误  
  
1.  从 `Module` 语句中删除 `Of` 关键字。  
  
2.  如果想要使用泛型模块的功能，最接近的是泛型类。 使用 [Class 语句](../Topic/Class%20Statement%20\(Visual%20Basic\).md) 而非 `Module` 语句。  
  
## 请参阅  
 [Module 语句](../Topic/Module%20Statement.md)   
 [Of](../Topic/Of%20Clause%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [如何：定义可对不同数据类型提供相同功能的类](../Topic/How%20to:%20Define%20a%20Class%20That%20Can%20Provide%20Identical%20Functionality%20on%20Different%20Data%20Types%20\(Visual%20Basic\).md)