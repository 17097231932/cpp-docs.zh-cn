---
title: "“Implements”在运算符声明上无效 | Microsoft Docs"
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
  - "vbc33004"
  - "bc33004"
helpviewer_keywords: 
  - "BC33004"
ms.assetid: 22f27f4d-4bbd-4f8f-a6e8-0fc10efb268d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Implements”在运算符声明上无效
[Operator 语句](../Topic/Operator%20Statement.md) 指定 [Implements](../Topic/Implements%20Clause%20\(Visual%20Basic\).md) 关键字。  
  
 仅 `Function` 或 `Sub` 过程、属性或事件可以实现接口成员。 有关实现的详细信息，请参阅[不在生成中：Visual Basic 中的接口实现示例](http://msdn.microsoft.com/zh-cn/50bf2a30-73b6-4126-a921-075fd6eec278)。  
  
 `Operator` 过程需要 `Public` 和 `Shared` 两个关键字，而转换运算符需要 `Widening` 或 `Narrowing` 关键字。 有关详细信息，请参阅[运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)。  
  
 **错误 ID：**BC33004  
  
### 更正此错误  
  
-   如果你想要此过程实现接口成员，则将其重写为 `Function` 或 `Sub` 过程、属性或事件。  
  
-   如果你想要此过程定义运算符，请从其声明中删除 `Implements` 关键字。  
  
## 请参阅  
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)