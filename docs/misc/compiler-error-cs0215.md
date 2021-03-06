---
title: "Errore del compilatore CS0215 | Microsoft Docs"
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
  - "CS0215"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0215"
ms.assetid: 2060440d-be22-4c10-8b26-43b08b615447
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Errore del compilatore CS0215
Il tipo restituito dell'operatore True o False deve essere booleano  
  
 Gli operatori [true](/dotnet/csharp/language-reference/keywords/true) e [false](/dotnet/csharp/language-reference/keywords/false) definiti dall'utente devono avere un tipo restituito [bool](/dotnet/csharp/language-reference/keywords/bool). Per altre informazioni, vedere [Operatori che supportano l'overload](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators).  
  
 L'esempio seguente genera l'errore CS0215:  
  
```  
// CS0215.cs class MyClass { public static int operator true (MyClass MyInt)   // CS0215 // try the following line instead // public static bool operator true (MyClass MyInt) { return true; } public static int operator false (MyClass MyInt)   // CS0215 // try the following line instead // public static bool operator false (MyClass MyInt) { return true; } public static void Main() { } }  
```