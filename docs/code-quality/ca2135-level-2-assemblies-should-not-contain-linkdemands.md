---
title: "CA2135: Gli assembly di livello 2 non devono contenere LinkDemands | Microsoft Docs"
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
  - "CA2135"
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2135: Gli assembly di livello 2 non devono contenere LinkDemands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2135|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Una classe o un membro della classe sta utilizzando un <xref:System.Security.Permissions.SecurityAction> in un'applicazione che utilizza una sicurezza di livello 2.  
  
## Descrizione della regola  
 I LinkDemand sono deprecati nel set di regole per la sicurezza di livello 2.  Anziché utilizzare LinkDemands per garantire la sicurezza nella compilazione JIT \(Just\-In\-Time\), contrassegnare i metodi, i tipi e campi con l'attributo <xref:System.Security.SecurityCriticalAttribute>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere <xref:System.Security.Permissions.SecurityAction> e contrassegnare il tipo o il membro con l'attributo <xref:System.Security.SecurityCriticalAttribute>.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio seguente, <xref:System.Security.Permissions.SecurityAction> deve essere rimosso e il metodo contrassegnato con l'attributo <xref:System.Security.SecurityCriticalAttribute>.  
  
 [!code-cs[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]