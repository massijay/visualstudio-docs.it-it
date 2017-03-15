---
title: "CA1056: Le propriet&#224; URI non devono essere stringhe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UriPropertiesShouldNotBeStrings"
  - "CA1056"
helpviewer_keywords: 
  - "CA1056"
  - "UriPropertiesShouldNotBeStrings"
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA1056: Le propriet&#224; URI non devono essere stringhe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriPropertiesShouldNotBeStrings|  
|CheckId|CA1056|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo dichiara una proprietà stringa il cui nome contiene "uri", "Uri", "urn", "Urn", "url" o "Url".  
  
## Descrizione della regola  
 La regola suddivide il nome della proprietà in token in base alla convenzione di denominazione Pascal e verifica che ogni token sia uguale a "uri", "Uri", "urn", "Urn", "url" o "Url".  Se è presente una corrispondenza, la regola presuppone che la proprietà rappresenti un URI \(Uniform Resource Identifier\).  Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza.  La classe <xref:System.Uri?displayProperty=fullName> fornisce questi servizi in un modo sicuro e protetto.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare la proprietà in un tipo <xref:System.Uri>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se la proprietà non rappresenta un URI.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati un tipo `ErrorProne` che viola la regola e un tipo `SaferWay` che la soddisfa.  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]  
  
## Regole correlate  
 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)