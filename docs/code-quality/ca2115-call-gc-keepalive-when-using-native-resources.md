---
title: "CA2115: Chiamare GC.KeepAlive durante l&#39;utilizzo di risorse native | Microsoft Docs"
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
  - "CallGCKeepAliveWhenUsingNativeResources"
  - "CA2115"
helpviewer_keywords: 
  - "CA2115"
  - "CallGCKeepAliveWhenUsingNativeResources"
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2115: Chiamare GC.KeepAlive durante l&#39;utilizzo di risorse native
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGCKeepAliveWhenUsingNativeResources|  
|CheckId|CA2115|  
|Category|Microsoft.Security|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo dichiarato in un tipo con un finalizzatore fa riferimento a un campo <xref:System.IntPtr?displayProperty=fullName> o <xref:System.UIntPtr?displayProperty=fullName>, ma non chiama <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.  
  
## Descrizione della regola  
 Garbage Collection completa un oggetto se nel codice gestito non sono presenti ulteriori riferimenti a esso.  I riferimenti non gestiti agli oggetti non impediscono Garbage Collection.  Questa regola rileva gli errori che possono verificarsi qualora una risorsa non gestita venga completata mentre è ancora utilizzata da codice non gestito.  
  
 Questa regola presuppone che nei campi <xref:System.IntPtr> e <xref:System.UIntPtr> siano archiviati puntatori a risorse non gestite.  Poiché lo scopo di un finalizzatore consiste nel liberare risorse non gestite, la regola presuppone che il finalizzatore liberi le risorse non gestite indicate dai campi del puntatore.  Questa regola presuppone inoltre che il metodo faccia riferimento al campo del puntatore per passare la risorsa non gestita a codice non gestito.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere al metodo una chiamata a <xref:System.GC.KeepAlive%2A>, passando l'istanza corrente \(`this` in C\# e C\+\+\) come argomento.  Posizionare la chiamata dopo l'ultima riga di codice in cui l'oggetto deve essere protetto da Garbage Collection.  Immediatamente dopo la chiamata a <xref:System.GC.KeepAlive%2A>, l'oggetto viene nuovamente considerato pronto per Garbage Collection, presupponendo che non siano presenti riferimenti gestiti a esso.  
  
## Esclusione di avvisi  
 Questa regola si basa su alcune presupposizioni che possono portare a falsi positivi.  L'esclusione di un avviso da questa regola è sicura nei seguenti casi:  
  
-   Il finalizzatore non libera il contenuto del campo <xref:System.IntPtr> o <xref:System.UIntPtr> a cui il metodo fa riferimento.  
  
-   Il metodo non passa il campo <xref:System.IntPtr> o <xref:System.UIntPtr> a codice non gestito.  
  
 Rivedere accuratamente gli altri messaggi prima di escluderli.  Questa regola rileva errori difficili da riprodurre e da sottoporre a debug.  
  
## Esempio  
 Nell'esempio seguente, `BadMethod` non include una chiamata a `GC.KeepAlive` e pertanto non viene violata la regola.  `GoodMethod` contiene il codice corretto.  
  
> [!NOTE]
>  Questo esempio è pseudo\-codice sebbene il codice venga compilato ed eseguito, l'avviso non viene generato perché una risorsa non gestita non viene creata o liberata.  
  
 [!code-cs[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]  
  
## Vedere anche  
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 [Modello Dispose](../Topic/Dispose%20Pattern.md)