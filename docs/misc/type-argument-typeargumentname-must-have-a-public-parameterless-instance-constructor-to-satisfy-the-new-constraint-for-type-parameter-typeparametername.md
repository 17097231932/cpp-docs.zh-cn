---
title: "类型实参“&lt;typeargumentname&gt;”必须具有一个公共的无参数实例构造函数，才能满足类型形参“&lt;typeparametername&gt;”的“New”约束。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32083"
  - "BC32083"
helpviewer_keywords: 
  - "BC32083"
ms.assetid: 56bf25f1-375c-4b5d-9969-45eba8b3b66c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 类型实参“&lt;typeargumentname&gt;”必须具有一个公共的无参数实例构造函数，才能满足类型形参“&lt;typeparametername&gt;”的“New”约束。
类型实参向不具有可访问的无参数构造函数的类型提供具有 [New 运算符](../Topic/New%20Operator%20\(Visual%20Basic\).md) 约束的类型形参。  
  
 约束列表对传递给类型形参的类型实参有一定要求。 一个可能的要求是类型参数必须公开一个创建代码可访问的无参数构造函数。 若要指定此要求，则该约束列表包括 `New` 约束。  
  
 **错误 ID：**BC32083  
  
### 更正此错误  
  
1.  验证类型参数中的泛型类型名称和类型名称拼写正确。  
  
2.  为类型参数选择一个类型，该类型用于公开可访问的无参数构造函数。 不能调用此特定的泛型类型，除非可为此类型形参提供此类的类型实参。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [类型列表](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [如何：使用泛型类](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)