---
title: "类“&lt;classname1&gt;”必须声明一个“Sub New”，因它的基类“&lt;classname2&gt;”有多个不使用参数就可以调用的可访问“Sub New” | Microsoft Docs"
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
  - "bc32036"
  - "vbc32036"
helpviewer_keywords: 
  - "BC32036"
ms.assetid: 9b96387e-337e-4b2a-b49f-783c7e13811a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 类“&lt;classname1&gt;”必须声明一个“Sub New”，因它的基类“&lt;classname2&gt;”有多个不使用参数就可以调用的可访问“Sub New”
派生的类没有声明构造函数，且由于无法确定要调用的基类构造函数，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 不能生成构造函数。  
  
 当派生的类没有声明构造函数时，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 尝试生成一个调用 `MyBase.New()` 的隐式无参数构造函数。 如果基类中没有无需参数即可调用的可访问的构造函数，或者如果有多个，则 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 无法生成隐式构造函数。  
  
 例如，如果一个基类构造函数具有单个 `Optional` 参数，而另一个具有单个 `ParamArray` 参数，则可能会出现这种情况。 可以在没有参数的情况下调用各个构造函数。  
  
 **错误 ID：**BC32036  
  
### 更正此错误  
  
1.  声明和实现派生类中某个位置的至少一个 `Sub New` 构造函数。  
  
2.  添加对基类构造函数 `MyBase.New()` 的调用，作为每个 `Sub New` 的第一行。  
  
## 请参阅  
 [对象生存期：如何创建和销毁对象](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [不在生成中：使用构造函数和析构函数](http://msdn.microsoft.com/zh-cn/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [Optional](../Topic/Optional%20\(Visual%20Basic\).md)   
 [ParamArray](../Topic/ParamArray%20\(Visual%20Basic\).md)   
 [可选参数](../Topic/Optional%20Parameters%20\(Visual%20Basic\).md)   
 [参数数组](../Topic/Parameter%20Arrays%20\(Visual%20Basic\).md)