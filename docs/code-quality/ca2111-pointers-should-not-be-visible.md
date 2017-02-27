---
title: "CA2111: I puntatori non devono essere visibili | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PointersShouldNotBeVisible"
  - "CA2111"
helpviewer_keywords: 
  - "CA2111"
  - "PointersShouldNotBeVisible"
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2111: I puntatori non devono essere visibili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PointersShouldNotBeVisible|  
|CheckId|CA2111|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un campo pubblico o protetto <xref:System.IntPtr?displayProperty=fullName> o <xref:System.UIntPtr?displayProperty=fullName> non è in sola lettura.  
  
## Descrizione della regola  
 <xref:System.IntPtr> e <xref:System.UIntPtr> sono tipi di puntatore utilizzati per accedere alla memoria non gestita.  Se un puntatore non è privato, interno o in sola lettura, è possibile che codice dannoso ne modifichi il valore, consentendo potenzialmente l'accesso a percorsi arbitrari nella memoria o causando errori dell'applicazione o di sistema.  
  
 Se si intende proteggere l'accesso al tipo che contiene il campo del puntatore, vedere [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## Come correggere le violazioni  
 Proteggere il puntatore contrassegnandolo come in sola lettura, interno o privato.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola se non ci si basa sul valore del puntatore.  
  
## Esempio  
 Nel codice riportato di seguito vengono illustrati puntatori che violano e soddisfano la regola.  Si noti che i puntatori non privati violano anche la regola [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
 [!code-cs[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## Regole correlate  
 [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## Vedere anche  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>