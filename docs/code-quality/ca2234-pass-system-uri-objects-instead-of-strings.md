---
title: "CA2234: Passare oggetti System.Uri invece di stringhe | Microsoft Docs"
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
  - "PassSystemUriObjectsInsteadOfStrings"
  - "CA2234"
helpviewer_keywords: 
  - "CA2234"
  - "PassSystemUriObjectsInsteadOfStrings"
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2234: Passare oggetti System.Uri invece di stringhe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PassSystemUriObjectsInsteadOfStrings|  
|CheckId|CA2234|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Viene effettuata una chiamata a un metodo che presenta un parametro di stringa il cui nome contiene "uri", "Uri", "urn", "Urn", "url" o "Url" e il tipo dichiarante del metodo contiene un overload di metodo corrispondente che presenta un parametro <xref:System.Uri?displayProperty=fullName>.  
  
## Descrizione della regola  
 Un nome di parametro è suddiviso in token in base alla convenzione Camel, pertanto viene verificato se ogni token è uguale a "uri", "Uri", "urn", "Urn", "url" o "Url".  Se è presente una corrispondenza, si presuppone che il parametro rappresenti un URI \(Uniform Resource Identifier\).  Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza.  La classe <xref:System.Uri> fornisce questi servizi in un modo sicuro e protetto.  Quando è presente una scelta tra due overload che differiscono esclusivamente nella rappresentazione di un URI, l'utente deve scegliere l'overload che utilizza un argomento <xref:System.Uri>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare l'overload che utilizza l'argomento <xref:System.Uri>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il parametro di stringa non rappresenta un URI.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati il metodo `ErrorProne` che viola la regola e il metodo `SaferWay` che chiama correttamente l'overload <xref:System.Uri>.  
  
 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-cs[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]  
  
## Regole correlate  
 [CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)  
  
 [CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)