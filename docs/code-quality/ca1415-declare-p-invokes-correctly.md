---
title: "CA1415: Dichiarare correttamente i P/Invoke | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
helpviewer_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1415: Dichiarare correttamente i P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Non sostanziale: se il P\/Invoke che dichiara il parametro non è visibile all'esterno dell'assembly.  Sostanziale: se il P\/Invoke che dichiara il parametro è visibile all'esterno dell'assembly.|  
  
## Causa  
 Un metodo di platform invoke non è stato dichiarato correttamente.  
  
## Descrizione della regola  
 Un metodo di platform invoke accede al codice non gestito e viene definito mediante la parola chiave `Declare` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o mediante <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  Attualmente questa regola ricerca le dichiarazioni del metodo di platform invoke per le funzioni Win32 con un puntatore a un parametro di struttura OVERLAPPED e il cui parametro gestito corrispondente non è un puntatore a una struttura <xref:System.Threading.NativeOverlapped?displayProperty=fullName>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, dichiarare correttamente il metodo di platform invoke.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono visualizzati i metodi di richiamo piattaforma che violano e soddisfano la regola.  
  
 [!CODE [FxCop.Interoperability.DeclarePInvokes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes#1)]  
  
## Vedere anche  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)