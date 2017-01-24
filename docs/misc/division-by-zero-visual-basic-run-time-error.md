---
title: "除数为零（Visual Basic 运行时错误） | Microsoft Docs"
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
  - "vbrID11"
ms.assetid: 5b9bc5d6-792e-48bc-a974-012e07ad95f3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 除数为零（Visual Basic 运行时错误）
用作除数的表达式有一个值为零。  
  
### 更正此错误  
  
1.  检查表达式中变量的拼写是否正确。 拼写错误的变量名可能会隐式创建一个初始化为零的数值变量。  
  
2.  检查之前对表达式中的变量进行的操作，尤其是那些从其他过程作为参数传递给该过程的操作。  
  
## 请参阅  
 [通过值和通过引用传递参数](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)   
 [Parameter Passing Mechanism Changes in Visual Basic](http://msdn.microsoft.com/zh-cn/0fa2b0dc-aa1c-4797-bbd6-aa13c611cab2)