---
title: "Errore del compilatore CS0077 | Microsoft Docs"
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
# Errore del compilatore CS0077
L'operatore as deve essere usato con un tipo riferimento o con un tipo nullable \('int' è un tipo valore non nullable\).  
  
 All'operatore [as](/dotnet/csharp/language-reference/keywords/as) operatore è stato passato un [tipo valore](/dotnet/csharp/language-reference/keywords/value-types). Poiché`as` può restituire [null](/dotnet/csharp/language-reference/keywords/null), quindi è possibile passare a tale operatore solo [tipi riferimento](/dotnet/csharp/language-reference/keywords/reference-types) o un tipo nullable. Per altre informazioni sui tipi nullable, vedere [Tipi nullable](/dotnet/csharp/programming-guide/nullable-types/index).  
  
 L'esempio seguente genera l'errore CS0077:  
  
```  
// CS0077.cs using System; class C { } struct S { } class M { public static void Main() { object o1, o2; C c; S s; o1 = new C(); o2 = new S(); s = o2 as S;  // CS0077, S is not a reference type. // try the following line instead // c = o1 as C; } }  
```