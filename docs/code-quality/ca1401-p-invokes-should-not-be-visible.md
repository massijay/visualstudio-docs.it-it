---
title: "CA1401: I P/Invoke non devono essere visibili | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PInvokesShouldNotBeVisible"
  - "CA1401"
helpviewer_keywords: 
  - "CA1401"
  - "PInvokesShouldNotBeVisible"
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1401: I P/Invoke non devono essere visibili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokesShouldNotBeVisible|  
|CheckId|CA1401|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo pubblico o protetto in un tipo pubblico presenta l'attributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> \(implementato anche dalla parola chiave `Declare` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Descrizione della regola  
 I metodi contrassegnati con l'attributo <xref:System.Runtime.InteropServices.DllImportAttribute> \(o quelli definiti mediante la parola chiave `Declare` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) utilizzano i PInvoke per accedere a codice non gestito.  Questi metodi non devono essere esposti.  Mantenendo privati o interni questi metodi, si garantisce che la libreria non venga utilizzata per violare la sicurezza consentendo ai chiamanti di accedere ad API non gestite che altrimenti non potrebbero chiamare.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il livello di accesso del metodo.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene dichiarato un metodo che viola questa regola.  
  
 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-cs[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]