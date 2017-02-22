---
title: "CA2138: I metodi Transparent non devono chiamare i metodi con l&#39;attributo SuppressUnmanagedCodeSecurity | Microsoft Docs"
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
  - "CA2138"
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2138: I metodi Transparent non devono chiamare i metodi con l&#39;attributo SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo SecurityTransparent chiama un metodo contrassegnato dall'attributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.  
  
## Descrizione della regola  
 Questa regola funziona su qualsiasi metodo trasparente che chiama direttamente in codice nativo, ad esempio tramite chiamata P\/Invoke \(platform invoke\).  P\/Invoke e metodi di interoperabilità COM contrassegnati dall'attributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> risultano in un LinkDemand eseguito sul metodo chiamante.  Poiché il codice SecurityTransparent non può soddisfare LinkDemands, il codice non può chiamare inoltre metodi contrassegnati dall'attributo SuppressUnmanagedCodeSecurity o metodi di classe contrassegnati dall'attributo SuppressUnmanagedCodeSecurity.  Il metodo non riuscirà o la richiesta sarà convertita in una richiesta completa.  
  
 Violazioni di questa regola conducono a <xref:System.MethodAccessException> nel modello SecurityTransparent di Livello 2 e ad una richiesta completa per <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> nel modello della trasparenza di livello 1.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere l'attributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> e contrassegnare il metodo con l'attributo <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 [!code-cs[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]