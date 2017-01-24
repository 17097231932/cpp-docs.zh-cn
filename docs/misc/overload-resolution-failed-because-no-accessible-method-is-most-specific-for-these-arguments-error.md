---
title: "重载决策失败，原因是这些参数没有最具体的可访问“&lt;method&gt;”：&lt;error&gt; | Microsoft Docs"
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
  - "bc30521"
  - "vbc30521"
helpviewer_keywords: 
  - "决策失败"
  - "BC30521"
  - "重载决策失败"
ms.assetid: b8b41fa0-a64b-4e74-8443-be3afd2b6f11
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 重载决策失败，原因是这些参数没有最具体的可访问“&lt;method&gt;”：&lt;error&gt;
你对重载方法进行了调用，但编译器找到了具有形参列表的两个或多个重载（你的实参列表可以转换为此形参列表），并且它无法在它们之间选择。  
  
 编译器尝试尽可能匹配调用实参列表和重载形参列表中的数据类型。 它需要从每个实参扩大转换为其对应的形参，而无论类型检查开关 \([Option Strict 语句](../Topic/Option%20Strict%20Statement.md)\) 是 `On` 还是 `Off`。  
  
 如果编译器找到满足扩大要求的多个重载，则会查找对实参数据类型最具体的重载，即需要进行最少量的扩大转换的重载。 当某一重载更加特定于某一实参的数据类型，而另一个重载更加特定于另一个实参的数据类型时，它将生成此错误消息。 有关详细信息及示例，请参阅[重载决策](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)。  
  
 **错误 ID：**BC30521  
  
### 更正此错误  
  
1.  查看该方法的所有重载并确定你想要调用的重载。  
  
2.  在调用语句中，使实参的数据类型与为所需重载定义的形参的数据类型匹配。 建议使用 [CType 函数](../Topic/CType%20Function%20\(Visual%20Basic\).md) 将一个或多个数据类型转换为已定义的类型。  
  
## 请参阅  
 [过程重载](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [重载过程注意事项](../Topic/Considerations%20in%20Overloading%20Procedures%20\(Visual%20Basic\).md)   
 [重载决策](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)   
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [重载属性和方法](../Topic/Overloaded%20Properties%20and%20Methods%20\(Visual%20Basic\).md)   
 [Option Strict 语句](../Topic/Option%20Strict%20Statement.md)   
 [CType 函数](../Topic/CType%20Function%20\(Visual%20Basic\).md)