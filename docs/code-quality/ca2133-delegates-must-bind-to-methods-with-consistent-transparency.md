---
title: "CA2133: Delegati devono essere associati ai metodi con trasparenza consistente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2133"
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2133: Delegati devono essere associati ai metodi con trasparenza consistente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DelegatesMustBindWithConsistentTransparency|  
|CheckId|CA2133|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
> [!NOTE]
>  Questo avviso è applicato solo al codice che sta eseguendo CoreCLR \(la versione di CLR che è specifica delle applicazioni Web di Silverlight\).  
  
## Causa  
 Questo avviso si attiva su un metodo che associa un delegato contrassegnato da <xref:System.Security.SecurityCriticalAttribute> a un metodo che è trasparente o contrassegnato con <xref:System.Security.SecuritySafeCriticalAttribute>.  L'avviso genera anche un metodo che associa un delegato che è trasparente o critico per la sicurezza a un metodo critico.  
  
## Descrizione della regola  
 Tipi delegati e i metodi ai quali li associano devono disporre di trasparenza coerente.  È possibile che i delegati trasparenti SafeCritical associno solo agli altri metodi trasparenti o SafeCritical.  Analogamente, è possibile che delegati critici si associno solo ai metodi critici.  Queste regole di associazione assicurano che l'unico codice che può richiamare un metodo tramite un delegato può inoltre aver richiamato direttamente lo stesso metodo.  Ad esempio, le regole di associazione non consentono la chiamata direttamente da codice critico tramite un delegato trasparente.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questo avviso, modificare la trasparenza del delegato o del metodo che vi associa in modo che la trasparenza dei due è equivalente.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
### Codice  
 [!code-cs[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]