---
title: "编译器错误 CS0213 | Microsoft Docs"
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
  - "CS0213"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0213"
ms.assetid: 3c1d55e3-2b84-4c28-8206-ef65869a898c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0213
不能使用 fixed 语句来获取已固定的表达式的地址  
  
 [unsafe](../Topic/unsafe%20\(C%23%20Reference\).md) 方法中的局部变量或某个参数已固定（在堆栈上），因此无法在 [fixed](../Topic/fixed%20Statement%20\(C%23%20Reference\).md) 表达式中获取这两个变量的任何一个的地址。 有关详细信息，请参阅[不安全代码和指针](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md)。  
  
## 示例  
 下面的示例生成 CS0213。  
  
```  
// CS0213.cs // compile with: /unsafe public class MyClass { unsafe public static void Main() { int i = 45; fixed (int *j = &i) { }  // CS0213 // try the following line instead // int* j = &i; int[] a = new int[] {1,2,3}; fixed (int *b = a) { fixed (int *c = b) { }  // CS0213 // try the following line instead // int *c = b; } } }  
```