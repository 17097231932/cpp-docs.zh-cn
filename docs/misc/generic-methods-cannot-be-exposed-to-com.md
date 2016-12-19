---
title: "不能向 COM 公开泛型方法 | Microsoft Docs"
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
  - "vbc30943"
  - "bc30943"
helpviewer_keywords: 
  - "BC30943"
ms.assetid: 0e3bff62-f187-4864-8520-70f6be22e869
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能向 COM 公开泛型方法
包含一个或多个泛型过程的 [!INCLUDE[dnprdnshort](../Token/dnprdnshort_md.md)] 组件导出到了 COM 组件。  
  
 组件对象模型 \(COM\) 不支持泛型类型，并且不能与其交互操作。  
  
 **错误 ID：**BC30943  
  
### 更正此错误  
  
-   从 [!INCLUDE[dnprdnshort](../Token/dnprdnshort_md.md)] 组件中删除一个或多个泛型过程，或者不在 COM 交互操作中使用泛型过程。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [COM 互操作](../Topic/COM%20Interop%20\(Visual%20Basic\).md)