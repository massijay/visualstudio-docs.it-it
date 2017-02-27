---
title: "CA1054: I parametri URI non devono essere stringhe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1054: I parametri URI non devono essere stringhe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriParametersShouldNotBeStrings|  
|CheckId|CA1054|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo dichiara un metodo con un parametro di stringa il cui nome contiene "uri", "Uri", "urn", "Urn", "url" o "Url" e tale tipo non dichiara un overload corrispondente che accetta un parametro <xref:System.Uri?displayProperty=fullName>.  
  
## Descrizione della regola  
 La regola suddivide il nome del parametro in token in base alla convenzione di denominazione Camel e controlla che ogni token sia uguale a "uri", "Uri", "urn", "Urn", "url" o "Url".  Se è presente una corrispondenza, la regola presuppone che il parametro rappresenti un URI \(Uniform Resource Identifier\).  Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza.  Se un metodo accetta una rappresentazione di stringa di un URI, deve essere fornito un overload corrispondente che accetti un'istanza della classe <xref:System.Uri>, la quale fornisce questi servizi in modo sicuro e protetto.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il parametro in un tipo <xref:System.Uri>. Si tratta di una modifica sostanziale.  In alternativa, fornire un overload del metodo che accetta un parametro <xref:System.Uri>. Si tratta di una modifica non sostanziale.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il parametro non rappresenta un URI.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati un tipo `ErrorProne` che viola la regola e un tipo `SaferWay` che la soddisfa.  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]  
  
## Regole correlate  
 [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: Passare oggetti System.Uri invece di stringhe](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)