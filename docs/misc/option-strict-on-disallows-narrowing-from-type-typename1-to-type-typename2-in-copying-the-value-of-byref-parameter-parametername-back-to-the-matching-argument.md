---
title: "将 ByRef 形参“&lt;parametername&gt;”的值复制回匹配实参时，Option Strict On 不允许从类型“&lt;typename1&gt;”收缩为类型“&lt;typename2&gt;”。 | Microsoft Docs"
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
  - "bc32029"
  - "vbc32029"
helpviewer_keywords: 
  - "BC32029"
ms.assetid: fc9ae5d2-b506-47cf-a50c-116fda5ed206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 将 ByRef 形参“&lt;parametername&gt;”的值复制回匹配实参时，Option Strict On 不允许从类型“&lt;typename1&gt;”收缩为类型“&lt;typename2&gt;”。
过程调用提供了一个 `ByRef` 实参，其数据类型扩大到了实参的声明类型，并且 `Option Strict` 为 `On`。 实参传递给过程时，允许进行扩大转换，但如果过程修改了调用代码中可变实参的内容，其反向转换将为收缩转换。 不允许对 `Option Strict On` 进行收缩转换。  
  
 **错误 ID：**BC32029  
  
### 更正此错误  
  
-   为过程调用中的每个 `ByRef` 实参提供与声明类型相同的数据类型，或转换为 `Option Strict Off`。  
  
## 请参阅  
 [Option Strict 语句](../Topic/Option%20Strict%20Statement.md)   
 [通过值和通过引用传递参数](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)   
 [扩大转换和收缩转换](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [隐式转换和显式转换](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)