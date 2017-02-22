---
title: "CA2104: Non dichiarare tipi di riferimento modificabili in sola lettura | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
  - "CA2104"
helpviewer_keywords: 
  - "CA2104"
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2104: Non dichiarare tipi di riferimento modificabili in sola lettura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|Category|Microsoft.Security|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo visibile esternamente contiene un campo in sola lettura visibile esternamente che costituisce un tipo di riferimento modificabile.  
  
## Descrizione della regola  
 Un tipo modificabile è un tipo i cui dati di istanza possono essere modificati.  La classe <xref:System.Text.StringBuilder?displayProperty=fullName> è un esempio di tipo di riferimento modificabile.  Contiene membri che possono modificare il valore di un'istanza della classe.  Un esempio di tipo di riferimento non modificabile è la classe <xref:System.String?displayProperty=fullName>.  Il suo valore non potrà mai cambiare dopo che è stata creata un'istanza.  
  
 Il modificatore in sola lettura \([readonly](/dotnet/csharp/language-reference/keywords/readonly) in C\#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e [const](/visual-cpp/cpp/const-cpp) in C\+\+\) in un campo di tipo di riferimento \(puntatore in C\+\+\) impedisce che il campo venga sostituito da un'istanza diversa del tipo di riferimento.  Tuttavia, il modificatore non consente di evitare la modifica dei dati dell'istanza del campo tramite il tipo riferimento.  
  
 I campi di matrici in sola lettura non sono interessati questa regola, ma causano invece una violazione della regola [CA2105: I campi di matrici non devono essere di sola lettura](../code-quality/ca2105-array-fields-should-not-be-read-only.md).  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il modificatore in sola lettura oppure, se è accettabile una modifica sostanziale, sostituire il campo con un tipo non modificabile.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il tipo di campo non è modificabile.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrata una dichiarazione di campo che causa una violazione di questa regola.  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-cs[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]