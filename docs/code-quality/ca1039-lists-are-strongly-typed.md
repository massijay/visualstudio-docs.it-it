---
title: "CA1039: Gli elenchi sono fortemente tipizzati | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
helpviewer_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1039: Gli elenchi sono fortemente tipizzati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ListsAreStronglyTyped|  
|CheckId|CA1039|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Il tipo pubblico o protetto implementa <xref:System.Collections.IList?displayProperty=fullName>, ma non fornisce un metodo fortemente tipizzato per uno o più degli elementi riportati di seguito:  
  
-   IList.Item  
  
-   IList.Add  
  
-   IList.Contains  
  
-   IList.IndexOf  
  
-   IList.Insert  
  
-   IList.Remove  
  
## Descrizione della regola  
 La regola richiede che le implementazioni di <xref:System.Collections.IList> forniscano membri fortemente tipizzati in modo che agli utenti non venga richiesto di eseguire il cast di argomenti al tipo <xref:System.Object?displayProperty=fullName> quando utilizzano la funzionalità fornita dall'interfaccia.  L'interfaccia <xref:System.Collections.IList> è implementata da raccolte di oggetti a cui è possibile accedere tramite l'indice.  La regola presuppone che il tipo che implementa <xref:System.Collections.IList> esegua questa operazione per gestire una raccolta di istanze di un tipo più sicuro di <xref:System.Object>.  
  
 <xref:System.Collections.IList> implementa le interfacce <xref:System.Collections.ICollection?displayProperty=fullName> e <xref:System.Collections.IEnumerable?displayProperty=fullName>.  Se si implementa <xref:System.Collections.IList>, è necessario fornire i membri fortemente tipizzati necessari per <xref:System.Collections.ICollection>.  Se gli oggetti della raccolta estendono <xref:System.ValueType?displayProperty=fullName>, è necessario fornire un membro fortemente tipizzato per il metodo <xref:System.Collections.IEnumerable.GetEnumerator%2A> allo scopo di evitare un calo delle prestazioni causato dal boxing. Questa operazione non è necessaria quando gli oggetti della raccolta sono un tipo di riferimento.  
  
 Per conformità a questa regola, implementare in modo esplicito i membri dell'interfaccia utilizzando nomi nel formato NomeInterfaccia.NomeMembroInterfaccia, ad esempio <xref:System.Collections.IList.Add%2A>.  I membri di interfaccia espliciti utilizzano i tipi di dati dichiarati dall'interfaccia.  Implementare i membri fortemente tipizzati mediante il nome del membro dell'interfaccia, ad esempio `Add`.  Dichiarare i membri fortemente tipizzati come pubblici e dichiarare i parametri e i valori restituiti in modo che siano del tipo sicuro gestito dalla raccolta.  I tipi sicuri sostituiscono i tipi meno sicuri quali <xref:System.Object> e <xref:System.Array> dichiarati dall'interfaccia.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare in modo esplicito i membri <xref:System.Collections.IList> e fornire alternative fortemente tipizzate per i membri indicati in precedenza.  Affinché il codice implementi correttamente l'interfaccia <xref:System.Collections.IList> e fornisca i membri fortemente tipizzati necessari, vedere l'esempio riportato di seguito.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola quando si implementa una nuova raccolta basata su oggetti, ad esempio un elenco collegato in cui i tipi che estendono la nuova raccolta determinano il tipo sicuro.  Questi tipi devono essere conformi a questa regola ed esporre membri fortemente tipizzati.  
  
## Esempio  
 Nell'esempio riportato di seguito, il tipo `YourType` estende <xref:System.Collections.CollectionBase?displayProperty=fullName>, come richiesto a tutte le raccolte fortemente tipizzate.  Si noti che <xref:System.Collections.CollectionBase> consente di fornire l'implementazione esplicita dell'interfaccia <xref:System.Collections.IList>.  Pertanto, è necessario fornire solo i membri fortemente tipizzati per <xref:System.Collections.IList> e <xref:System.Collections.ICollection>.  
  
 [!code-cs[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]  
  
## Regole correlate  
 [CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1038: Gli enumeratori devono essere fortemente tipizzati](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
## Vedere anche  
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.IList?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>