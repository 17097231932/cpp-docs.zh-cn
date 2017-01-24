---
title: "编译器错误 CS0666 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0666"
ms.assetid: 44ad4574-b4a2-487b-8d05-0116762231ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0666
“member”：结构中已声明新的保护成员  
  
 [结构](../Topic/struct%20\(C%23%20Reference\).md)不能为[抽象](../Topic/abstract%20\(C%23%20Reference\).md)，并且它始终隐式[密封](../Topic/sealed%20\(C%23%20Reference\).md)。 由于结构不支持继承，因此结构中的[保护](../Topic/protected%20\(C%23%20Reference\).md)成员概念没有意义。 有关详细信息，请参阅[继承](../Topic/Inheritance%20\(C%23%20Programming%20Guide\).md)。  
  
## 示例  
 下面的示例生成 CS0666：  
  
```  
// CS0666.cs class M { static void Main() { } } struct S { protected int x;   // CS0666 }  
```