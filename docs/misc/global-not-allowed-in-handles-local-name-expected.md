---
title: "句柄中不允许“Global”；应为本地名称 | Microsoft Docs"
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
  - "bc36002"
  - "vbc36002"
helpviewer_keywords: 
  - "BC36002"
ms.assetid: 7b4602a9-84c9-4068-81bc-e8df03ffc130
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 句柄中不允许“Global”；应为本地名称
`Handles` 子句必须引用本地事件。`Global` 关键字提供了对全局编程元素的访问权限。  
  
 **错误 ID：**BC36002  
  
### 更正此错误  
  
-   将 `Handles` 子句更改为引用事件的本地实例而不是全局实例。  
  
## 请参阅  
 [Global \- delete](http://msdn.microsoft.com/zh-cn/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md)   
 [事件](../Topic/Events%20\(Visual%20Basic\).md)