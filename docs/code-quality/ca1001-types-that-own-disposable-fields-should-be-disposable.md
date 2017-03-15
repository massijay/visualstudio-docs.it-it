---
title: "CA1001: I tipi proprietari di campi Disposable devono essere Disposable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1001"
  - "TypesThatOwnDisposableFieldsShouldBeDisposable"
helpviewer_keywords: 
  - "CA1001"
  - "TypesThatOwnDisposableFieldsShouldBeDisposable"
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1001: I tipi proprietari di campi Disposable devono essere Disposable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale \- Se il tipo non è visibile all'esterno dell'assembly.<br /><br /> Sostanziale \- Se il tipo è visibile all'esterno dell'assembly.|  
  
## Causa  
 Una classe dichiara e implementa un campo di istanza che corrisponde a un tipo <xref:System.IDisposable?displayProperty=fullName> e la classe non implementa <xref:System.IDisposable>.  
  
## Descrizione della regola  
 Una classe implementa l'interfaccia <xref:System.IDisposable> per eliminare le risorse non gestite di cui è proprietaria.  Un campo di istanza che corrisponde a un tipo <xref:System.IDisposable> indica che il campo è proprietario di una risorsa non gestita.  Una classe che dichiara un campo <xref:System.IDisposable> è indirettamente proprietaria di una risorsa non gestita e dovrebbe implementare l'interfaccia <xref:System.IDisposable>.  Se la classe non è direttamente proprietaria di risorse non gestite, non dovrebbe implementare un finalizzatore.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare <xref:System.IDisposable> e dal metodo <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chiamare il metodo <xref:System.IDisposable.Dispose%2A> del campo.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrate due classi: una che viola la regola e una che la soddisfa mediante l'implementazione di <xref:System.IDisposable>.  La classe non implementa un finalizzatore in quanto non è direttamente proprietaria di risorse non gestite.  
  
 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-cs[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]  
  
## Regole correlate  
 [CA2213: I campi Disposable devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: I metodi Dispose devono chiamare il metodo Dispose della classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: I tipi delle risorse native devono essere Disposable](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)