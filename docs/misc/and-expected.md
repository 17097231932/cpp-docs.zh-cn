---
title: "应为“And” | Microsoft Docs"
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
  - "vbc36620"
  - "bc36620"
helpviewer_keywords: 
  - "BC36620"
ms.assetid: b3d21d4d-86c0-44d2-8afc-c19d375e9ddd
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 应为“And”
除 `And` 外的某个比较运算符已用于合并 `Join` 或 `Group Join` 子句中的两个或多个 `Equals` 运算符。 仅允许 `And` 运算符合并 `Join` 或 `Group Join` 子句中的多个 `Equals` 运算符。  
  
 **错误 ID：**BC36620  
  
### 更正此错误  
  
1.  重组 `Equals` 子句，从而只使用 `And` 运算符来进行比较。 下面是一个示例：  
  
    ```vb#  
    Dim petOwnersJoin = From pers In people _  
                        Join pet In pets _  
                        On pet.Owner Equals pers And _  
                           pet.Name = pers.PetName_  
                        Select pers, pet  
    ```  
  
## 请参阅  
 [如何：使用联接合并数据](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Join 子句](../Topic/Join%20Clause%20\(Visual%20Basic\).md)   
 [Group Join 子句](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)   
 [Visual Basic 中的 LINQ 简介](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)