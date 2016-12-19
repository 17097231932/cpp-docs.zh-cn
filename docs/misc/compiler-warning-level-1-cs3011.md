---
title: "编译器警告（等级 1）CS3011 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3011"
ms.assetid: e27ce521-0147-488b-b4a1-1b6fb5168661
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器警告（等级 1）CS3011
“member”：只有符合 CLS 的成员才能是抽象的  
  
 类成员不能既[抽象](../Topic/abstract%20\(C%23%20Reference\).md)又不遵从公共语言规范 \(CLS\)。 CLS 指定应实现的所有类成员。 有关 CLS 遵从性的详细信息，请参见[编写符合 CLS 的代码](http://msdn.microsoft.com/zh-cn/4c705105-69a2-4e5e-b24e-0633bc32c7f3)和 [语言独立性和与语言无关的组件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  
  
## 示例  
 下面的示例生成 CS3011：  
  
```  
// CS3011.cs using System; [assembly:CLSCompliant(true)] public abstract class I { [CLSCompliant(false)] public abstract int M();   // CS3011 // OK [CLSCompliant(false)] public void M2() { } } public class C : I { public override int M() { return 1; } public static void Main() { } }  
```