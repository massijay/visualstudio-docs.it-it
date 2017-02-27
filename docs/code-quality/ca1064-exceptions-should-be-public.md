---
title: "CA1064: Le eccezioni devono essere pubbliche | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1064"
  - "ExceptionsShouldBePublic"
helpviewer_keywords: 
  - "CA1064"
  - "ExceptionsShouldBePublic"
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1064: Le eccezioni devono essere pubbliche
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ExceptionsShouldBePublic|  
|CheckId|CA1064|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un'eccezione non pubblica deriva direttamente da <xref:System.Exception>, <xref:System.SystemException> o <xref:System.ApplicationException>.  
  
## Descrizione della regola  
 Un'eccezione interna è visibile solo nel relativo ambito interno.  Se l'eccezione si verifica al di fuori dell'ambito interno, può essere rilevata solo tramite l'eccezione di base.  Se l'eccezione interna è ereditata da <xref:System.Exception>, <xref:System.SystemException> o <xref:System.ApplicationException>, il codice esterno non disporrà di informazioni sufficienti per la corretta gestione dell'eccezione.  
  
 Se invece nel codice è presente un'eccezione pubblica utilizzata in seguito come base per un'eccezione interna, è ragionevole supporre che il codice più esterno sarà in grado di gestire in modo più opportuno l'eccezione di base.  All'eccezione pubblica saranno associate maggiori informazioni rispetto a quelle fornite da T:System.Exception, T:System.SystemException o T:System.ApplicationException.  
  
## Come correggere le violazioni  
 Rendere pubblica l'eccezione o derivare l'eccezione interna da un'eccezione pubblica diversa da <xref:System.Exception>, <xref:System.SystemException> o <xref:System.ApplicationException>.  
  
## Esclusione di avvisi  
 Escludere un messaggio da questa regola se si è certi che, in qualsiasi caso, l'eccezione privata sarà rilevata nel relativo ambito interno.  
  
## Esempio  
 Questa regola si attiva nel primo metodo di esempio, FirstCustomException, perché la classe dell'eccezione deriva direttamente da Exception ed è interna.  La regola non viene eseguita nella classe SecondCustomException perché, sebbene anche la classe derivi direttamente da Exception, la classe viene dichiarata pubblica.  Anche la terza classe non attiva la regola perché non deriva direttamente da <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName> o <xref:System.ApplicationException?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]