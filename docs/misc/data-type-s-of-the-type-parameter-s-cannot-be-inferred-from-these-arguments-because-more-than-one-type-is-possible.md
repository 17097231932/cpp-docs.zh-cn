---
title: "无法从这些参数推断出类型参数的数据类型，因为可能有多种类型。 | Microsoft Docs"
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
  - "vbc36653"
  - "bc36653"
  - "vbc36650"
  - "bc36650"
helpviewer_keywords: 
  - "BC36650"
  - "BC36653"
ms.assetid: 79287e1f-7070-4a71-96d2-aee0a0c9d8bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法从这些参数推断出类型参数的数据类型，因为可能有多种类型。
无法根据这些参数推断出类型参数的数据类型，因为可能有多种类型。 显式指定数据类型可更正此错误。  
  
 当重载决策失败时发生此错误。 它以从属消息的形式发生，该消息指示特定重载候选项被消除的原因。 该错误解释，如果应用类型推断来确定被调用的泛型过程的类型参数的数据类型，则编译器将为至少一个类型参数找到多个可能的数据类型。  
  
> [!NOTE]
>  当无法指定实参时（例如，对于查询表达式中的查询运算符），显示的错误消息不包括第二个句子。  
  
 有关更多信息和示例，请参见[无法根据这些参数推断出方法“\<方法名\>”中类型参数的数据类型，因为可能有多种类型](../misc/data-type-s-of-the-type-parameter-s-in-method-methodname-cannot-be-inferred-from-these-arguments-because-more-than-one-type-is-possible.md)。  
  
 **错误 ID：**BC36653 和 BC36650  
  
## 请参阅  
 [Visual Basic 中的泛型过程](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [重载决策](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)