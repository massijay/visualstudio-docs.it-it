---
title: "CA1038: Gli enumeratori devono essere fortemente tipizzati | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EnumeratorsShouldBeStronglyTyped"
  - "CA1038"
helpviewer_keywords: 
  - "CA1038"
  - "EnumeratorsShouldBeStronglyTyped"
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1038: Gli enumeratori devono essere fortemente tipizzati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico o protetto implementa <xref:System.Collections.IEnumerator?displayProperty=fullName>, ma non fornisce una versione fortemente tipizzata della proprietà <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>.  I tipi derivati dai tipi riportati di seguito non sono interessati da questa regola:  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## Descrizione della regola  
 Questa regola richiede che le implementazioni di <xref:System.Collections.IEnumerator> forniscano anche una versione fortemente tipizzata della proprietà <xref:System.Collections.IEnumerator.Current%2A> in modo che agli utenti non venga richiesto di eseguire il cast del valore restituito nel tipo sicuro quando utilizzano la funzionalità fornita dall'interfaccia.  Questa regola presuppone che il tipo che implementa <xref:System.Collections.IEnumerator> contenga una raccolta di istanze di un tipo più sicuro di <xref:System.Object>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare in modo esplicito la proprietà dell'interfaccia \(dichiararla come `IEnumerator.Current`\).  Aggiungere una versione fortemente tipizzata pubblica della proprietà, dichiarata come `Current`, e fare in modo che restituisca un oggetto fortemente tipizzato.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola quando si implementa un enumeratore basato su oggetti da utilizzare con una raccolta basata su oggetti, quale una struttura ad albero binaria.  I tipi che estendono la nuova raccolta definiranno l'enumeratore fortemente tipizzato ed esporranno la proprietà fortemente tipizzata.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato il modo corretto per implementare un tipo <xref:System.Collections.IEnumerator> fortemente tipizzato.  
  
 [!code-cs[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]  
  
## Regole correlate  
 [CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039: Gli elenchi sono fortemente tipizzati](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## Vedere anche  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>