---
title: "CA1819: Le propriet&#224; non devono restituire matrici | Microsoft Docs"
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
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
helpviewer_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1819: Le propriet&#224; non devono restituire matrici
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotReturnArrays|  
|CheckId|CA1819|  
|Category|Microsoft.Performance|  
|Breaking Change|Breaking|  
  
## Causa  
 Una proprietà pubblica o protetta in un tipo pubblico restituisce una matrice.  
  
## Descrizione della regola  
 Le matrici restituite dalle proprietà non sono protette in scrittura, anche se la proprietà è in sola lettura.  Affinché la matrice sia protetta da eventuali alterazioni, la proprietà deve restituire una copia della matrice.  In genere, gli utenti non comprendono le implicazioni negative sulle prestazioni derivanti dalla chiamata di tale proprietà.  In particolare, potrebbero utilizzare la proprietà come una proprietà indicizzata.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, trasformare la proprietà in metodo oppure modificare la proprietà affinché restituisca una raccolta.  
  
## Esclusione di avvisi  
 Gli attributi possono contenere proprietà che restituiscono matrici, ma non proprietà che restituiscono raccolte.  È possibile eliminare un avviso generato per una proprietà di un attributo derivante dalla classe [System.Attribute](assetId:///System.Attribute?qualifyHint=False&autoUpgrade=True).  Altrimenti, non escludere un avviso da questa regola.  
  
## Esempio di violazione  
  
### Descrizione  
 Nell'esempio riportato di seguito viene illustrata una proprietà che viola questa regola.  
  
### Codice  
 [!code-cs[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### Commenti  
 Per correggere una violazione di questa regola, trasformare la proprietà in metodo oppure modificare la proprietà affinché restituisca una raccolta anziché una matrice.  
  
## Esempio di trasformazione di una proprietà in metodo  
  
### Descrizione  
 Nell'esempio seguente viene corretta la violazione cambiando la proprietà in metodo.  
  
### Codice  
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-cs[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]  
  
## Esempio di restituzione di una raccolta  
  
### Descrizione  
 Nell'esempio seguente viene corretta la violazione cambiando la proprietà in modo che restituisca un insieme.  
  
 <xref:System.Collection.ObjectModel.ReadOnlyCollection?displayProperty=fullName>.  
  
### Codice  
 [!code-cs[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]  
  
## Consentire agli utenti di modificare una proprietà  
  
### Descrizione  
 Potrebbe essere necessario consentire a un consumer della classe di modificare una proprietà.  Nell'esempio riportato di seguito viene illustrata una proprietà in lettura e scrittura che viola questa regola.  
  
### Codice  
 [!code-cs[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]  
  
### Commenti  
 Nell'esempio seguente viene corretta la violazione modificando la proprietà in modo che restituisca un oggetto <xref:System.Collection.ObjectModel.Collection?displayProperty=fullName>.  
  
### Codice  
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-cs[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]  
  
## Regole correlate  
 [CA1024: Utilizzare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)