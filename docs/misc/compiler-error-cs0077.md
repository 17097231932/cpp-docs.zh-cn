---
title: "编译器错误 CS0077 | Microsoft Docs"
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
  - "CS0077"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0077"
ms.assetid: 55d3d290-d172-41a3-b326-ebf5a0a7e81f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0077
as 运算符必须与引用类型或可以为 null 的类型一起使用（“int”是不可以为 null 值的类型）。  
  
 向 [as](../Topic/as%20\(C%23%20Reference\).md) 运算符传递了[值类型](../Topic/Value%20Types%20\(C%23%20Reference\).md)。 因为 `as` 可以返回 [null](../Topic/null%20\(C%23%20Reference\).md)，所以只能向其传递[引用类型](../Topic/Reference%20Types%20\(C%23%20Reference\).md)或可以为 null 的类型。 有关可以为 null 的类型的详细信息，请参见 [可以为 null 的类型](../Topic/Nullable%20Types%20\(C%23%20Programming%20Guide\).md)。  
  
 下面的示例生成 CS0077：  
  
```  
// CS0077.cs using System; class C { } struct S { } class M { public static void Main() { object o1, o2; C c; S s; o1 = new C(); o2 = new S(); s = o2 as S;  // CS0077, S is not a reference type. // try the following line instead // c = o1 as C; } }  
```