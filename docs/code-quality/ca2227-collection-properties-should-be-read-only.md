---
title: "CA2227: Le propriet&#224; di raccolte devono essere in sola lettura | Microsoft Docs"
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
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
helpviewer_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2227: Le propriet&#224; di raccolte devono essere in sola lettura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionPropertiesShouldBeReadOnly|  
|CheckId|CA2227|  
|Category|Microsoft.Usage|  
|Breaking Change|Breaking|  
  
## Causa  
 Una proprietà modificabile visibile a livello esterno è un tipo che implementa l'oggetto <xref:System.Collections.ICollection?displayProperty=fullName>.  Matrici, indicizzatori \(proprietà con il nome 'Item'\) e set di autorizzazioni vengono ignorati dalla regola.  
  
## Descrizione della regola  
 Una proprietà di raccolta modificabile consente a un utente di sostituire la raccolta con una raccolta completamente differente.  Una proprietà di sola lettura interrompe la sostituzione della raccolta ma consente ancora l'impostazione dei singoli membri.  Se la sostituzione della raccolta è un obiettivo, il modello di progettazione preferito prevede l'inclusione di un metodo per rimuovere tutti gli elementi dalla raccolta e un metodo per reinserire i dati nella raccolta.  Vedere i metodi <xref:System.Collections.ArrayList.Clear%2A> e <xref:System.Collections.ArrayList.AddRange%2A> della classe <xref:System.Collections.ArrayList?displayProperty=fullName> per un esempio di questo modello.  
  
 La serializzazione XML e binaria supportano le proprietà di sola lettura che sono raccolte.  La classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> presenta requisiti specifici per i tipi che implementano <xref:System.Collections.ICollection> e <xref:System.Collections.IEnumerable?displayProperty=fullName> in modo che siano serializzabili.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rendere la proprietà di sola lettura e, se la progettazione lo richiede, aggiungere metodi per cancellare e reinserire i dati nella raccolta.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene visualizzata una proprietà di raccolta modificabile e viene illustrato il modo in cui è possibile sostituire direttamente la raccolta.  Inoltre, viene visualizzata la maniera preferita di sostituire una proprietà di raccolta di sola lettura utilizzando i metodi `Clear` e `AddRange`.  
  
 [!code-cs[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]  
  
## Regole correlate  
 [CA1819: Le proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md)