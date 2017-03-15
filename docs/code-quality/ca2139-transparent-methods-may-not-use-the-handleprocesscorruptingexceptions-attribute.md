---
title: "CA2139: I metodi Transparent non possono utilizzare l&#39;attributo HandleProcessCorruptingExceptions | Microsoft Docs"
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
  - "CA2139"
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2139: I metodi Transparent non possono utilizzare l&#39;attributo HandleProcessCorruptingExceptions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|  
|CheckId|CA2139|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo Trasparent è contrassegnato con l'attributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>.  
  
## Descrizione della regola  
 Questa regola attiva qualsiasi metodo trasparente e tenta di gestire un processo che danneggiando l'eccezione tramite l'attributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>.  Un processo che danneggia un'eccezione è una classificazione di eccezioni versione CLR 4.0 di eccezioni come <xref:System.AccessViolationException>.  L'attributo HandleProcessCorruptedStateExceptionsAttribute può essere utilizzato solo dai metodi critici per la sicurezza e sarà ignorato se applicato a un metodo trasparente.  Per gestire le eccezioni che danneggiano il processo, questo metodo deve diventare SecurityCritical o SecuritySafeCritical.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere l'attributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> o contrassegnare il metodo con l'attributo <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 In questo esempio, un metodo trasparente viene contrassegnato con l'attributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> e la regola avrà esito negativo.  Il metodo deve essere contrassegnato anche con l'attributo <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
 [!code-cs[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]