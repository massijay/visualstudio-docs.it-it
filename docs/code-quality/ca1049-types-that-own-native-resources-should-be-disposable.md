---
title: "CA1049: I tipi delle risorse native devono essere Disposable | Microsoft Docs"
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
  - "CA1049"
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
helpviewer_keywords: 
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
  - "CA1049"
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1049: I tipi delle risorse native devono essere Disposable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|  
|CheckId|CA1049|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo fa riferimento a un campo <xref:System.IntPtr?displayProperty=fullName>, a un campo <xref:System.UIntPtr?displayProperty=fullName> o a un campo <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, ma non implementa l'interfaccia <xref:System.IDisposable?displayProperty=fullName>.  
  
## Descrizione della regola  
 Questa regola presuppone che nei campi <xref:System.IntPtr>, <xref:System.UIntPtr> e <xref:System.Runtime.InteropServices.HandleRef> siano archiviati puntatori a risorse non gestite.  I tipi che allocano risorse non gestite devono implementare l'interfaccia <xref:System.IDisposable> per consentire ai chiamanti di rilasciare quelle risorse su richiesta e di ridurre la durata degli oggetti che le contengono.  
  
 Il modello di progettazione consigliato per la pulitura delle risorse non gestite consiste nel fornire mezzi impliciti ed espliciti per liberare le risorse utilizzando rispettivamente il metodo <xref:System.Object.Finalize%2A?displayProperty=fullName> e il metodo <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>.  Il Garbage Collector chiama il metodo <xref:System.Object.Finalize%2A> di un oggetto in un determinato momento dopo che l'oggetto è stato definito come non più raggiungibile.  Dopo la chiamata al metodo <xref:System.Object.Finalize%2A>, è necessaria un'operazione aggiuntiva di Garbage Collection per liberare l'oggetto.  Il metodo <xref:System.IDisposable.Dispose%2A> consente al chiamante di rilasciare esplicitamente le risorse su richiesta, prima di quando verrebbero rilasciate dal Garbage Collector.  Dopo aver eseguito la pulitura delle risorse non gestite, <xref:System.IDisposable.Dispose%2A> deve chiamare il metodo <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> per comunicare al Garbage Collector che non è più necessario chiamare il metodo <xref:System.Object.Finalize%2A>. In questo modo, l'operazione di Garbage Collection aggiuntiva non è più necessaria e si riduce la durata dell'oggetto.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare <xref:System.IDisposable>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il tipo non fa riferimento a una risorsa non gestita.  In caso contrario, non escludere un avviso da questa regola poiché la mancata implementazione dell'interfaccia <xref:System.IDisposable> può rendere non disponibili o sottoutilizzate le risorse non gestite.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che implementa l'interfaccia <xref:System.IDisposable> per eseguire la pulitura di una risorsa non gestita.  
  
 [!code-cs[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## Regole correlate  
 [CA2115: Chiamare GC.KeepAlive durante l'utilizzo di risorse native](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816: Chiamare GC.SuppressFinalize correttamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001: I tipi proprietari di campi Disposable devono essere Disposable](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)  
  
## Vedere anche  
 [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)   
 [Modello Dispose](../Topic/Dispose%20Pattern.md)