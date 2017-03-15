---
title: "CA2143: I metodi Transparent non devono utilizzare SecurityDemand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2143"
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA2143: I metodi Transparent non devono utilizzare SecurityDemand
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotDemand|  
|CheckId|CA2143|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Il metodo o il tipo Trasparent è contrassegnato in modo dichiarativo da una richiesta <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName>`.Demand` oppure il metodo chiama il metodo <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>.  
  
## Descrizione della regola  
 Il codice SecurityTransparent non deve essere responsabile della verifica della sicurezza di un'operazione e quindi non deve richiedere autorizzazioni.  Il codice trasparente per la sicurezza deve utilizzare richieste complete per prendere decisioni relative alla sicurezza e il codice critico per la sicurezza non deve basarsi sul codice trasparente per l'esecuzione della richiesta completa.  Qualsiasi codice che esegue controlli di sicurezza, come ad esempio le richieste di sicurezza, devono essere invece SafeCritical.  
  
## Come correggere le violazioni  
 In generale, per correggere una violazione di questa regola, contrassegnare il metodo con l'attributo <xref:System.Security.SecuritySafeCriticalAttribute>.  È anche possibile rimuovere la richiesta.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 I file delle regole nel seguente codice perché un metodo trasparente fa una richiesta di sicurezza dichiarativa.  
  
 [!code-cs[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## Vedere anche  
 [CA2142: Il codice Transparent non deve essere protetto con LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)