---
title: "类型“&lt;typename&gt;”必须定义运算符“&lt;determinantoperator&gt;”才能在“&lt;shortcircuitoperator&gt;”表达式中使用 | Microsoft Docs"
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
  - "bc33035"
  - "vbc33035"
helpviewer_keywords: 
  - "BC33035"
ms.assetid: 50a0a39f-63cd-4100-aea9-91b5b6ab5bbf
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 类型“&lt;typename&gt;”必须定义运算符“&lt;determinantoperator&gt;”才能在“&lt;shortcircuitoperator&gt;”表达式中使用
[AndAlso 运算符](../Topic/AndAlso%20Operator%20\(Visual%20Basic\).md) 或 [OrElse 运算符](../Topic/OrElse%20Operator%20\(Visual%20Basic\).md) 使用类或结构类型的操作数，此时该类或结构不会定义所需的运算符。  
  
 由于未直接定义短路运算符（`AndAlso` 或 `OrElse`），因此必须定义相应的逻辑和行列式运算符。 下表显示了所需的运算符。  
  
|短路运算符|逻辑运算符|行列式运算符|  
|-----------|-----------|------------|  
|`AndAlso`|[And 运算符](../Topic/And%20Operator%20\(Visual%20Basic\).md)|[IsFalse 运算符](../Topic/IsFalse%20Operator%20\(Visual%20Basic\).md)|  
|`OrElse`|[Or 运算符](../Topic/Or%20Operator%20\(Visual%20Basic\).md)|[IsTrue 运算符](../Topic/IsTrue%20Operator%20\(Visual%20Basic\).md)|  
  
 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 使用这些逻辑运算符和行列式运算符来构造用于 `AndAlso` 或 `OrElse` 的短路逻辑。 为使其正常工作，`And` 或 `Or` 定义的操作数和返回值必须为包含类型，也就是说，你可在其中定义 `And` 或 `Or` 的类或结构的类型。  
  
 **错误 ID：**BC33035  
  
### 更正此错误  
  
-   利用 `AndAlso` 或 `OrElse` 运算符的操作数类型锁使用的类和结构定义 `And` 和 `IsFalse` 运算符，或定义 `Or` 和 `IsTrue` 运算符。 请确保 `And` 或 `Or` 的操作数属于你定义的类或结构的类型。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Visual Basic 中的逻辑运算符和位运算符](../Topic/Logical%20and%20Bitwise%20Operators%20in%20Visual%20Basic.md)