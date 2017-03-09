---
title: "CA1816: Chiamare GC.SuppressFinalize correttamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
helpviewer_keywords: 
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1816: Chiamare GC.SuppressFinalize correttamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|Category|Microsoft.  Utilizzo|  
|Breaking Change|Non sostanziale|  
  
## Causa  
  
-   Un metodo che rappresenta un'implementazione di <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> non chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Un metodo che non rappresenta un'implementazione di <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Un metodo chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> passando un argomento diverso da questo \(Me in Visual Basic\).  
  
## Descrizione della regola  
 Il metodo <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> consente agli utenti di rilasciare risorse in qualsiasi momento prima che l'oggetto diventi disponibile per un'operazione di Garbage Collection.  Se viene chiamato il metodo <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, le risorse dell'oggetto vengono liberate.  In questo modo non è necessario effettuare la finalizzazione.  <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> dovrebbe chiamare <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> affinché il finalizzatore dell'oggetto non venga chiamato dal Garbage Collector.  
  
 Per evitare che tipi derivati con finalizzatori debbano implementare nuovamente [System.IDisposable](assetId:///System.IDisposable?qualifyHint=True&autoUpgrade=False) e chiamarlo, è ancora necessario che i tipi non sealed senza finalizzatori chiamino <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola:  
  
 Se il metodo è un'implementazione di <xref:System.IDisposable.Dispose%2A>, aggiungere una chiamata a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 Se il metodo non è un'implementazione di <xref:System.IDisposable.Dispose%2A>, rimuovere la chiamata a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> oppure spostarla nell'implementazione di <xref:System.IDisposable.Dispose%2A> del tipo.  
  
 Modifica tutte le chiamate in <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> per passare l'elemento this \(Me in Visual Basic\).  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola solo se si utilizza deliberatamente <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> per controllare la durata di altri oggetti.  Non escludere un avviso da questa regola se un'implementazione di <xref:System.IDisposable.Dispose%2A> non chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  In questa situazione, la mancata esclusione della finalizzazione comporta un calo delle prestazioni e non offre alcun vantaggio.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un metodo che chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> in modo non corretto.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-cs[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un metodo che chiama correttamente <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!CODE [FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1)]  
  
## Regole correlate  
 [CA2215: I metodi Dispose devono chiamare il metodo Dispose della classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## Vedere anche  
 [Modello Dispose](../Topic/Dispose%20Pattern.md)