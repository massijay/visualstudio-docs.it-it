---
title: "CA2130: Le costanti SecurityCritical devono essere Transparent | Microsoft Docs"
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
  - "CA2130"
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2130: Le costanti SecurityCritical devono essere Transparent
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConstantsShouldBeTransparent|  
|CheckId|CA2130|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un campo costante o un membro di enumerazione è contrassegnato da <xref:System.Security.SecurityCriticalAttribute>.  
  
## Descrizione della regola  
 L'imposizione della trasparenza non viene applicata ai valori costanti perché i compilatori rendono inline valori costanti in modo che non sia richiesta alcuna ricerca in fase di esecuzione.  I campi costanti devono essere trasparenti per la sicurezza in modo che i revisori del codice non suppongano che il codice trasparente non possa accedere alla costante.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere l'attributo SecurityCritical dal campo o valore.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Negli esempi seguenti, il valore di enumerazione `EnumWithCriticalValues.CriticalEnumValue` e la costante `CriticalConstant` generano questo avviso.  Per correggere i problemi, rimuovere l'attributo \[`SecurityCritical`\] per renderlo SecurityTransparent.  
  
 [!code-cs[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]