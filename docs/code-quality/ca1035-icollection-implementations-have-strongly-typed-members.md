---
title: "CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICollectionImplementationsHaveStronglyTypedMembers"
  - "CA1035"
helpviewer_keywords: 
  - "CA1035"
  - "ICollectionImplementationsHaveStronglyTypedMembers"
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico o protetto implementa <xref:System.Collections.ICollection?displayProperty=fullName>, ma non fornisce un metodo fortemente tipizzato per <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>.  La versione fortemente tipizzata di <xref:System.Collections.ICollection.CopyTo%2A> deve accettare due parametri e non può avere <xref:System.Array?displayProperty=fullName> o una matrice di <xref:System.Object?displayProperty=fullName> come primo parametro.  
  
## Descrizione della regola  
 La regola richiede che le implementazioni di <xref:System.Collections.ICollection> forniscano membri fortemente tipizzati in modo che agli utenti non venga richiesto di eseguire il cast di argomenti al tipo <xref:System.Object> quando utilizzano la funzionalità fornita dall'interfaccia.  Questa regola presuppone che il tipo che implementa <xref:System.Collections.ICollection> esegua questa operazione per gestire una raccolta di istanze di un tipo più sicuro di <xref:System.Object>.  
  
 L'oggetto <xref:System.Collections.ICollection> implementa l'interfaccia <xref:System.Collections.IEnumerable?displayProperty=fullName>.  Se gli oggetti della raccolta estendono <xref:System.ValueType?displayProperty=fullName>, è necessario fornire un membro fortemente tipizzato per il metodo <xref:System.Collections.IEnumerable.GetEnumerator%2A> allo scopo di evitare un calo delle prestazioni causato dal boxing.  Non è richiesto quando gli oggetti della raccolta sono un tipo di riferimento.  
  
 Per implementare una versione fortemente tipizzata di un membro di interfaccia, implementare in modo esplicito i membri di interfaccia utilizzando nomi nel formato `InterfaceName.InterfaceMemberName`, ad esempio <xref:System.Collections.ICollection.CopyTo%2A>.  I membri di interfaccia espliciti utilizzano i tipi di dati dichiarati dall'interfaccia.  Implementare i membri fortemente tipizzati mediante il nome del membro dell'interfaccia, ad esempio <xref:System.Collections.ICollection.CopyTo%2A>.  Dichiarare i membri fortemente tipizzati come pubblici e dichiarare i parametri e i valori restituiti in modo che siano del tipo sicuro gestito dalla raccolta.  I tipi sicuri sostituiscono i tipi meno sicuri quali <xref:System.Object> e <xref:System.Array> dichiarati dall'interfaccia.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare in modo esplicito il membro di interfaccia \(dichiararlo come <xref:System.Collections.ICollection.CopyTo%2A>\).  Aggiungere il membro pubblico fortemente tipizzato, dichiarato come `CopyTo` e fare in modo che accetti una matrice fortemente tipizzata come primo parametro.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola se si implementa una nuova raccolta basata su oggetti, ad esempio un albero binario, in cui i tipi che estendono la nuova raccolta determinano il tipo sicuro.  Questi tipi devono essere conformi a questa regola ed esporre membri fortemente tipizzati.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato il modo corretto di implementare <xref:System.Collections.ICollection>.  
  
 [!code-cs[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## Regole correlate  
 [CA1038: Gli enumeratori devono essere fortemente tipizzati](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039: Gli elenchi sono fortemente tipizzati](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## Vedere anche  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>