---
title: "CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1057"
  - "StringUriOverloadsCallSystemUriOverloads"
helpviewer_keywords: 
  - "StringUriOverloadsCallSystemUriOverloads"
  - "CA1057"
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StringUriOverloadsCallSystemUriOverloads|  
|CheckId|CA1057|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo dichiara overload di metodo che differiscono solo per la sostituzione di un parametro di stringa con un parametro <xref:System.Uri?displayProperty=fullName> e l'overload che accetta il parametro di stringa non chiama l'overload che accetta il parametro <xref:System.Uri>.  
  
## Descrizione della regola  
 Poiché gli overload differiscono solo per il parametro di stringa o<xref:System.Uri>, si presuppone che la stringa rappresenti un URI \(Uniform Resource Identifier\).  Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza.  La classe <xref:System.Uri> fornisce questi servizi in un modo sicuro e protetto.  Per usufruire dei vantaggi della classe <xref:System.Uri>, l'overload della stringa deve chiamare l'overload <xref:System.Uri> utilizzando l'argomento stringa.  
  
## Come correggere le violazioni  
 Reimplementare il metodo che utilizza la rappresentazione di stringa dell'URI in modo che crei un'istanza della classe <xref:System.Uri> utilizzando l'argomento stringa, quindi passi l'oggetto <xref:System.Uri> all'overload che presenta il parametro <xref:System.Uri>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il parametro di stringa non rappresenta un URI.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un overload di stringa implementato correttamente.  
  
 [!code-cs[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]  
  
## Regole correlate  
 [CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)