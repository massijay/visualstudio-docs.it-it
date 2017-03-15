---
title: "CA2141:I metodi Transparent non devono soddisfare i LinkDemand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2141"
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2141:I metodi Transparent non devono soddisfare i LinkDemand
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo Security Transparent chiama un metodo in un assembly che non è contrassegnato dall'attributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) oppure un metodo Security Transparent soddisfa un <xref:System.Security.Permissions.SecurityAction>`.LinkDemand` per un tipo o un metodo.  
  
## Descrizione della regola  
 La soddisfazione di un LinkDemand è un'operazione basata sulla sicurezza che può causare l'elevazione non intenzionale dei privilegi.  Il codice SecurityTransparent non deve soddisfare LinkDemands, perché non è soggetto agli stessi requisiti del controllo di sicurezza del codice SecurityCritical.  I metodi trasparenti negli assembly del set di regole di sicurezza di livello 1 faranno in modo che tutti i LinkDemands che essi soddisfano vengano convertiti in richieste complete in fase di esecuzione, che può creare problemi di prestazione.  Negli assembly del set di regole di sicurezza di livello 2, metodi trasparenti non riusciranno a compilare tramite il compilatore JIT \(Just\-in\-time\) se tentano di soddisfare un LinkDemand.  
  
 Negli assembly che utilizzano la sicurezza di Livello 2, i tentativi da parte di un metodo SecurityTransparent di soddisfare un LinkDemand o di chiamare un metodo in un assembly non\-APTCA generano un <xref:System.MethodAccessException>; negli assembly di Livello 1, LinkDemand diventa una Richiesta completa.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, contrassegnare il metodo di accesso con l'attributo <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> o rimuovere LinkDemand dal metodo di accesso.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 In questo esempio, un metodo trasparente tenta di chiamare un metodo che dispone di un LinkDemand.  Questa regola funzionerà su questo codice.  
  
 [!code-cs[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]