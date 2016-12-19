---
title: "运算符“&lt;operatorsymbol&gt;”没有在所有代码路径上返回值 | Microsoft Docs"
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
  - "vbc42106"
  - "bc42106"
helpviewer_keywords: 
  - "BC42106"
ms.assetid: 175b2bc9-5233-462d-97de-9d97b003cc46
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 运算符“&lt;operatorsymbol&gt;”没有在所有代码路径上返回值
运算符“\<operatorsymbol\>”没有在所有代码路径上返回值。 使用该结果时，可能会在运行时发生 null 引用异常。  
  
 运算符过程至少有一个通过其代码不会返回值的可能路径。  
  
 你可以从一个运算符过程返回一个值，只能通过将其包含在[Return 语句](../Topic/Return%20Statement%20\(Visual%20Basic\).md) 中实现。  
  
 如果控制权传递给了 `End Operator` 语句，运算符过程将返回属性数据类型的默认值。 有关详细信息，请参阅[Function 语句](../Topic/Function%20Statement%20\(Visual%20Basic\).md) 中的“Behavior”。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的详细信息，请参见 [在 Visual Basic 中配置警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **错误 ID：**BC42106  
  
### 更正此错误  
  
-   请检查控制流逻辑并确保每个可能的路径以 `Return` 语句结尾。 具体而言，`End Operator` 之前的最后一个语句应为 `Return` 语句。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)