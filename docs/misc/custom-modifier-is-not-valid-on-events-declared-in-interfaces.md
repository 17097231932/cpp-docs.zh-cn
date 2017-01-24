---
title: "“Custom”修饰符在接口中声明的事件上无效 | Microsoft Docs"
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
  - "bc31121"
  - "vbc31121"
helpviewer_keywords: 
  - "BC31121"
ms.assetid: b5687034-a2b2-4961-88b7-0ba73023573e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Custom”修饰符在接口中声明的事件上无效
无法在接口中声明自定义事件，因为自定义事件必须提供其 `AddHandler`、`RemoverHandler` 和 `RaiseEvent` 方法的实现。  
  
 `Custom` 关键字可用于实现事件的派生类中。  
  
 **错误 ID：**BC31121  
  
### 更正此错误  
  
-   从接口的事件声明中删除 `Custom` 关键字。  
  
## 示例  
 此示例演示如何实现在接口中声明为自定义事件的事件。  
  
 [!code-vb[VbVbalrEventError#3](../misc/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-in-interfaces_1.vb)]  
  
## 请参阅  
 [自定义 \- 删除](http://msdn.microsoft.com/zh-cn/dc62be07-c896-4866-a533-982a661d143f)   
 [Event 语句](../Topic/Event%20Statement.md)   
 [Delegate 语句](../Topic/Delegate%20Statement.md)   
 [Class 语句](../Topic/Class%20Statement%20\(Visual%20Basic\).md)   
 [Interface 语句](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [事件](../Topic/Events%20\(Visual%20Basic\).md)