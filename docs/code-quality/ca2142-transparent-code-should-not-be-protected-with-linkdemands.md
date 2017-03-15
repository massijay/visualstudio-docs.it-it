---
title: "CA2142: Il codice Transparent non deve essere protetto con LinkDemand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2142"
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2142: Il codice Transparent non deve essere protetto con LinkDemand
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo Trasparent richiede <xref:System.Security.Permissions.SecurityAction> o un'altra richiesta di sicurezza.  
  
## Descrizione della regola  
 Questa regola funziona su metodi trasparenti di cui richiedono a LinkDemands l'accesso.  Il codice SecurityTransparent non deve essere responsabile della verifica della sicurezza di un'operazione e quindi non deve richiedere autorizzazioni.  Poiché si suppone che i metodi trasparenti siano neutri per la sicurezza, non devono prendere alcuna decisione relativa alla sicurezza.  Inoltre, il codice SafeCritical, che prende decisioni relative alla sicurezza, non deve basarsi su codice trasparente per avere preso precedentemente tale decisione.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere la richiesta di collegamento sul metodo trasparente o contrassegnare il metodo con l'attributo <xref:System.Security.SecuritySafeCriticalAttribute> se sta eseguendo controlli di sicurezza, come ad esempio richieste di sicurezza.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio seguente, la regola si attiva sul metodo perché è trasparente ed è contrassegnato con un LinkDemand <xref:System.Security.PermissionSet> che contiene  <xref:System.Security.Permissions.SecurityAction>.  
  
 [!code-cs[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 Non escludere un avviso da questa regola.