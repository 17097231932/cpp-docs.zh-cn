---
title: "编译器错误 CS0177 | Microsoft Docs"
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
  - "CS0177"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0177"
ms.assetid: 852a8c2a-2411-4800-af7c-4c572d9900d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0177
在控件离开当前方法之前，必须对 out 参数“parameter”赋值  
  
 未向标记有 [out](../Topic/out%20\(C%23%20Reference\).md) 关键字的参数分配方法主体中的值。 有关详细信息，请参阅[传递参数](../Topic/Passing%20Parameters%20\(C%23%20Programming%20Guide\).md)。  
  
 下面的示例生成 CS0177：  
  
```  
// CS0177.cs public class MyClass { public static void Foo(out int i)   // CS0177 { // uncomment the following line to resolve this error //   i = 0; } public static void Main() { int x = -1; Foo(out x); } }  
```