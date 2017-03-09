---
title: "CA2126: Per le richieste di collegamento dei tipi sono necessarie richieste di ereditariet&#224; | Microsoft Docs"
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
  - "CA2126"
  - "TypeLinkDemandsRequireInheritanceDemands"
helpviewer_keywords: 
  - "CA2126"
  - "TypeLinkDemandsRequireInheritanceDemands"
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2126: Per le richieste di collegamento dei tipi sono necessarie richieste di ereditariet&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypeLinkDemandsRequireInheritanceDemands|  
|CheckId|CA2126|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico unsealed è protetto con una richiesta di collegamento, dispone di un metodo sottoponibile a override e né il tipo né il metodo sono protetti da una richiesta di ereditarietà.  
  
## Descrizione della regola  
 Una richiesta di collegamento su un metodo o il relativo tipo dichiarante richiede che il chiamante immediato del metodo disponga dell'autorizzazione specifica.  Una richiesta di ereditarietà su un metodo richiede che un metodo che esegue l'override abbia l'autorizzazione specifica.  Una richiesta di ereditarietà su un tipo richiede che una classe derivante disponga dell'autorizzazione specifica.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, proteggere il tipo o il metodo con una richiesta di ereditarietà per la stessa autorizzazione della richiesta di collegamento.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola la regola.  
  
 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-cs[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]  
  
## Regole correlate  
 [CA2108: Controllare la sicurezza dichiarativa sui tipi di valori](../code-quality/ca2108-review-declarative-security-on-value-types.md)  
  
 [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA2122: Non esporre in modo indiretto metodi con richieste di collegamento](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)  
  
 [CA2123: Le richieste di collegamento negli verrine devono essere identiche a quelle nei metodi di base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)  
  
## Vedere anche  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Inheritance Demands](http://msdn.microsoft.com/it-it/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Demands](http://msdn.microsoft.com/it-it/e5283e28-2366-4519-b27d-ef5c1ddc1f48)