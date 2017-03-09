---
title: "CA2131: I tipi SecurityCritical possono non partecipare all&#39;equivalenza del tipo | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2131"
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2131: I tipi SecurityCritical possono non partecipare all&#39;equivalenza del tipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo partecipa in equivalenza del tipo e il tipo stesso o un membro o un campo del tipo, è contrassegnato dall'attributo <xref:System.Security.SecurityCriticalAttribute>.  
  
## Descrizione della regola  
 Questa regola viene attivata su qualsiasi tipo critico o a tipi che contengono metodi o campi critici che partecipano all'equivalenza del tipo.  Quando CLR rileva tale tipo, non riesce a caricarlo in fase di esecuzione con un <xref:System.TypeLoadException>.  In genere, questa regola funziona solo quando gli utenti implementano l'equivalenza del tipo manualmente piuttosto che basarsi su tlbimp e i compilatori per fare l'equivalenza del tipo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere l'attributo SecurityCritical.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Gli esempi seguenti mostrano un'interfaccia, un metodo e un campo che faranno attivare questa regola.  
  
 [!code-cs[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## Vedere anche  
 [Security\-Transparent Code, Level 2](../Topic/Security-Transparent%20Code,%20Level%202.md)