---
title: 'CA1816: Chiamare GC. SuppressFinalize correttamente | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e99f722d211b2e1bd548f1bf22c995246f3e0b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Chiamare GC.SuppressFinalize correttamente
|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|Categoria|Microsoft. Utilizzo|  
|Breaking Change|Non importante|  
  
## <a name="cause"></a>Causa  
  
-   Un metodo che è un'implementazione di <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> non chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Un metodo che non è un'implementazione di <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chiamate <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Chiama un metodo <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> e passa un valore diverso da this (Me in Visual Basic).  
  
## <a name="rule-description"></a>Descrizione della regola  
 Il <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metodo consente agli utenti di rilasciare le risorse in qualsiasi momento prima che l'oggetto diventi disponibile per garbage collection. Se il <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metodo viene chiamato, libera le risorse dell'oggetto. In questo modo la finalizzazione non necessaria. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>deve chiamare <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> in modo che il garbage collector non chiamare il finalizzatore dell'oggetto.  
  
 Per impedire che i tipi derivati con finalizzatori dover implementare nuovamente <xref:System.IDisposable> e chiamarlo, tipi non sealed senza finalizzatori devono ancora chiamare <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola:  
  
 Se il metodo è un'implementazione di <xref:System.IDisposable.Dispose%2A>, aggiungere una chiamata a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 Se il metodo non è un'implementazione di <xref:System.IDisposable.Dispose%2A>, rimuovere la chiamata a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> o spostarlo nel tipo <xref:System.IDisposable.Dispose%2A> implementazione.  
  
 Modificare tutte le chiamate a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> passare this (Me in Visual Basic).  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere un avviso da questa regola solo se si utilizza deliberatamente <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> per controllare la durata di altri oggetti. Non escludere un avviso da questa regola se un'implementazione di <xref:System.IDisposable.Dispose%2A> non chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. In questo caso, la mancata eliminazione della finalizzazione comporta una riduzione delle prestazioni e non offre alcun vantaggio.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un metodo in modo non corretto che chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un metodo che correttamente le chiamate <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA2215: I metodi Dispose devono chiamare il metodo Dispose della classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Modello Dispose](/dotnet/standard/design-guidelines/dispose-pattern)