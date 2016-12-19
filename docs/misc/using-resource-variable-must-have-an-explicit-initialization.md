---
title: "“Using”资源变量必须有一个显式初始化 | Microsoft Docs"
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
  - "vbc36011"
  - "bc36011"
helpviewer_keywords: 
  - "BC36011"
ms.assetid: 5db996a6-0802-4b67-91f1-4aa9c3dd6b09
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Using”资源变量必须有一个显式初始化
`Using` 语句至少指定了一个未使用 `New` 子句初始化的资源。  
  
 如果在将控件传递给 `Using` 块前尚未获取资源，则`Using` 语句必须获取资源。 若要执行此操作，必须从指定的类创建一个对象，这样就需要 `New` 子句。  
  
 **错误 ID：**BC36011  
  
### 更正此错误  
  
-   如果你已获取资源，在 `Using` 语句中使用计算结果为所获资源的引用变量或表达式。  
  
     `Dim newFont As New System.Drawing.Font`  
  
     `Using newFont`  
  
-   如果尚未获取资源，将 `New` 子句添加到 `Using` 语句中。  
  
     `Using newFont as`   `New`   `System.Drawing.Font`  
  
## 请参阅  
 [Using 语句](../Topic/Using%20Statement%20\(Visual%20Basic\).md)   
 [New 运算符](../Topic/New%20Operator%20\(Visual%20Basic\).md)   
 [如何：释放系统资源](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)