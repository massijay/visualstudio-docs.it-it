---
title: 'CA2213: I campi Disposable devono essere eliminati | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 77cd32f97e3798362371fc21f8b38c14ce22c7fb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: I campi Disposable devono essere eliminati
|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|Categoria|Microsoft. Usage|  
|Breaking Change|Non importante|  
  
## <a name="cause"></a>Causa  
 Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> dichiara i campi di tipi che implementano anche <xref:System.IDisposable>. Il <xref:System.IDisposable.Dispose%2A> metodo del campo non viene chiamato dal <xref:System.IDisposable.Dispose%2A> metodo del tipo dichiarante.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Un tipo è responsabile per l'eliminazione di tutte le risorse non gestite; Questa operazione viene eseguita implementando <xref:System.IDisposable>. Questa regola consente di controllare se un tipo eliminabile `T` dichiara un campo `F` che rappresenta un'istanza di un tipo eliminabile `FT`. Per ogni campo `F`, la regola tenta di individuare una chiamata a `FT.Dispose`. La regola cerca i metodi chiamati da `T.Dispose`e il livello inferiore (i metodi chiamati da metodi chiamati da `FT.Dispose`).  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare <xref:System.IDisposable.Dispose%2A> nei campi di tipi che implementano <xref:System.IDisposable> se l'utente è responsabile per l'allocazione e rilascio delle risorse non gestite contenute in un campo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È consigliabile escludere un avviso da questa regola se non è responsabili per rilasciare le risorse contenute in un campo o se la chiamata a <xref:System.IDisposable.Dispose%2A> si verifica un livello più profondo chiamante rispetto a quanto controllato dalla regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo `TypeA` che implementa <xref:System.IDisposable> (`FT` nella spiegazione).  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo `TypeB` che violano questa regola dichiarando un campo `aFieldOfADisposableType` (`F` nella spiegazione precedente) come un tipo eliminabile (`TypeA`) e non chiamando <xref:System.IDisposable.Dispose%2A> al campo. `TypeB`corrisponde a `T` nella spiegazione precedente.  
  
 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Modello Dispose](/dotnet/standard/design-guidelines/dispose-pattern)