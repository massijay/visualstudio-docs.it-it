---
title: "CA2216: I tipi Disposable devono dichiarare un finalizzatore | Microsoft Docs"
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
  - "DisposableTypesShouldDeclareFinalizer"
  - "CA2216"
helpviewer_keywords: 
  - "CA2216"
  - "DisposableTypesShouldDeclareFinalizer"
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2216: I tipi Disposable devono dichiarare un finalizzatore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableTypesShouldDeclareFinalizer|  
|CheckId|CA2216|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> e presenta campi che suggeriscono l'utilizzo di risorse non gestite non implementa un finalizzatore come descritto da <xref:System.Object.Finalize%2A?displayProperty=fullName>.  
  
## Descrizione della regola  
 Viene segnalata una violazione di questa regola se il tipo Disposable contiene campi dei tipi riportati di seguito:  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare un finalizzatore che chiami il metodo <xref:System.IDisposable.Dispose%2A>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il tipo non implementa <xref:System.IDisposable> allo scopo di rilasciare risorse non gestite.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola questa regola.  
  
 [!code-cs[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]  
  
## Regole correlate  
 [CA2115: Chiamare GC.KeepAlive durante l'utilizzo di risorse native](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816: Chiamare GC.SuppressFinalize correttamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049: I tipi delle risorse native devono essere Disposable](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## Vedere anche  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Modello Dispose](../Topic/Dispose%20Pattern.md)