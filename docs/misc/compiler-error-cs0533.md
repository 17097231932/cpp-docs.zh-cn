---
title: "编译器错误 CS0533 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0533"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0533"
ms.assetid: f8b38c5a-d365-4081-a101-6282bdd19069
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0533
“derived\-class member”隐藏继承的抽象成员“derived\-class member”  
  
 基[类](../Topic/class%20\(C%23%20Reference\).md)方法被隐藏。 检查声明中的语法，查看它是否正确。  
  
 有关详细信息，请参阅 [base](../Topic/base%20\(C%23%20Reference\).md)。  
  
 以下示例生成 CS0533：  
  
```  
// CS0533.cs namespace x { abstract public class a { abstract public void f(); } abstract public class b : a { new abstract public void f();   // CS0533 // try the following lines instead // override public void f() // { // } public static void Main() { } } }  
```