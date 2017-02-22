---
title: "CA1055: I valori restituiti URI non devono essere stringhe | Microsoft Docs"
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
  - "CA1055"
  - "UriReturnValuesShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1055"
  - "UriReturnValuesShouldNotBeStrings"
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1055: I valori restituiti URI non devono essere stringhe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriReturnValuesShouldNotBeStrings|  
|CheckId|CA1055|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Il nome di un metodo contiene "uri", "Uri", "urn", "Urn", "url" o "Url" e il metodo restituisce una stringa.  
  
## Descrizione della regola  
 La regola suddivide il nome del metodo in token in base alla convenzione di denominazione Pascal e verifica che ogni token sia uguale a "uri", "Uri", "urn", "Urn", "url" o "Url".  Se viene rilevata una corrispondenza, la regola presuppone che il metodo restituisca un URI \(Uniform Resource Identifier\).  Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza.  La classe <xref:System.Uri?displayProperty=fullName> fornisce questi servizi in un modo sicuro e protetto.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il tipo restituito in un oggetto <xref:System.Uri>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il valore restituito non rappresenta un URI.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati un tipo `ErrorProne` che viola la regola e un tipo `SaferWay` che la soddisfa.  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]  
  
## Regole correlate  
 [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)