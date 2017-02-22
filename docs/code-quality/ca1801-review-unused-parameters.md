---
title: "CA1801: Rivedere i parametri inutilizzati | Microsoft Docs"
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
  - "AvoidUnusedParameters"
  - "CA1801"
  - "ReviewUnusedParameters"
helpviewer_keywords: 
  - "CA1801"
  - "ReviewUnusedParameters"
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1801: Rivedere i parametri inutilizzati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale \- Se il membro non è visibile all'esterno dell'assembly, indipendentemente dalla modifica apportata.<br /><br /> Non sostanziale \- Se si modifica il membro affinché utilizzi il parametro nel suo corpo.<br /><br /> Sostanziale \- Se si rimuove il parametro ed è visibile all'esterno dell'assembly.|  
  
## Causa  
 Una firma di metodo include un parametro non utilizzato nel corpo del metodo.  La regola non esamina i seguenti metodi:  
  
-   Metodi a cui fa riferimento un delegato.  
  
-   Metodi utilizzati come gestori eventi.  
  
-   Metodi dichiarati con il modificatore `abstract` \(`MustOverride` in Visual Basic\).  
  
-   Metodi dichiarati con il modificatore `virtual` \(`Overridable` in Visual Basic\).  
  
-   Metodi dichiarati con il modificatore `override` \(`Overrides` in Visual Basic\).  
  
-   Metodi dichiarati con il modificatore `extern` \(istruzione `Declare` in Visual Basic\).  
  
## Descrizione della regola  
 Rivedere i parametri in metodi non virtuali non utilizzati nel corpo del metodo per assicurarsi che nell'errore di accesso ad essi non siano presenti elementi corretti.  I parametri non utilizzati comportano costi in termini di prestazioni e gestione.  
  
 Talvolta, una violazione di questa regola può indicare un bug di implementazione nel metodo.  Il parametro, ad esempio, dovrebbe essere stato utilizzato nel corpo del metodo.  Escludere gli avvisi da questa regola se il parametro deve essere presente per assicurare la compatibilità con le versioni precedenti.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il parametro non utilizzato \(modifica sostanziale\) oppure utilizzare il parametro nel corpo del metodo \(modifica non sostanziale\).  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura per il codice fornito in precedenza per il quale la correzione rappresenterebbe una modifica sostanziale.  
  
## Esempio  
 Nell'esempio che segue vengono illustrati due metodi.  Un metodo viola la regola mentre l'altro la soddisfa.  
  
 [!code-cs[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]  
  
## Regole correlate  
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: rimuovere locali non utilizzati](../code-quality/ca1804-remove-unused-locals.md)