---
title: "应为类型或“With” | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30988"
  - "bc30988"
helpviewer_keywords: 
  - "BC30988"
ms.assetid: ab9c0cee-9fe4-4764-a3c2-aec16e709d4c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 应为类型或“With”
在声明类的实例时，`New` 关键字必须后跟类型名称或 `With`。 例如，以下语句各将 `client` 声明为 `Customer` 类的实例。 类型名称 `Customer` 在 `New` 之后。  
  
```  
' Dim client As New Customer()  
' The next declaration uses an object initializer.  
Dim client As New Customer() With {.Name = "Litware, Inc."}  
```  
  
 自 [!INCLUDE[vb_orcas_long](../misc/includes/vb_orcas_long_md.md)] 起，你可以将对象声明为匿名类型的实例，此情况下未指定数据类型。 在匿名类型声明中，关键字 `With` 在 `New` 之后。  
  
```  
Dim person = New With {.Name ="Mike Nash", .Age = 27}  
```  
  
 **错误 ID：**BC30988  
  
### 更正此错误  
  
-   更改声明，以便 `With` 或类型名称在 `New` 之后。  
  
## 请参阅  
 [匿名类型](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md)   
 [对象初始值设定项：命名类型和匿名类型](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [New 运算符](../Topic/New%20Operator%20\(Visual%20Basic\).md)   
 [NotInBuild：Visual Basic 中的声明语句](http://msdn.microsoft.com/zh-cn/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)