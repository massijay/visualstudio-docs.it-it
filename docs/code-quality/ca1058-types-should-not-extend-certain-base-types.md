---
title: "CA1058: I tipi non devono estendere tipi di base specifici | Microsoft Docs"
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
  - "TypesShouldNotExtendCertainBaseTypes"
  - "CA1058"
helpviewer_keywords: 
  - "CA1058"
  - "TypesShouldNotExtendCertainBaseTypes"
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1058: I tipi non devono estendere tipi di base specifici
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesShouldNotExtendCertainBaseTypes|  
|CheckId|CA1058|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo visibile esternamente estende tipi di base specifici.  Attualmente questa regola riporta tipi che derivano dai seguenti:  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## Descrizione della regola  
 Per [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versione 1 si consigliava di derivare nuove eccezioni da <xref:System.ApplicationException>.  Tale consiglio non è più applicabile e le nuove eccezioni dovrebbero derivare da <xref:System.Exception?displayProperty=fullName> o da una delle relative sottoclassi nello spazio dei nomi <xref:System>.  
  
 Non creare una sottoclasse di <xref:System.Xml.XmlDocument> se si desidera creare una visualizzazione XML di un'origine dati o di un modello a oggetti sottostante.  
  
### Raccolte non generiche  
 Utilizzare e\/o estendere raccolte generiche ovunque possibile.  Non estendere raccolte non generiche nel codice, a meno che non si tratti di codice che si è già fornito in precedenza.  
  
 **Esempi di utilizzo non corretto**  
  
```c#  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **Esempi di utilizzo corretto**  
  
```c#  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, derivare il tipo da un tipo base diverso o da una raccolta generica diversa.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola per le violazioni che riguardano <xref:System.ApplicationException>.  L'esclusione di un avviso da questa regola è sicura per violazioni relative a <xref:System.Xml.XmlDocument>.  La soppressione di un avviso relativo a una raccolta non generica è sicura se il codice è stato rilasciato in precedenza.