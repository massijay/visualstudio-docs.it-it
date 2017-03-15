---
title: "CA2145: I metodi Transparent non devono includere SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs"
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
  - "CA2145"
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2145: I metodi Transparent non devono includere SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Il metodo Trasparent, contrassegnato da un metodo <xref:System.Security.SecuritySafeCriticalAttribute> oppure un tipo che contiene un metodo contrassegnato dall'attributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.  
  
## Descrizione della regola  
 Metodi decorati con l'attributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> dispongono di un LinkDemand implicito posizionato su qualsiasi metodo che lo chiama.  Questo LinkDemand richiede che il codice chiamante sia SecurityCritical.  Contrassegnare il metodo che utilizza SuppressUnmanagedCodeSecurity con l'attributo <xref:System.Security.SecurityCriticalAttribute> rende più ovvio questo requisito per i chiamanti del metodo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, contrassegnare il metodo o il tipo con <xref:System.Security.SecurityCriticalAttribute>:  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
### Codice  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### Commenti