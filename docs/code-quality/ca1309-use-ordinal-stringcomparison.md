---
title: "CA1309: Utilizza StringComparison ordinale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
helpviewer_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1309: Utilizza StringComparison ordinale
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un'operazione di confronto di stringhe di tipo non linguistico non imposta il parametro <xref:System.StringComparison> su **Ordinal** o **OrdinalIgnoreCase**.  
  
## Descrizione della regola  
 Molte operazioni sulle stringhe, soprattutto i metodi <xref:System.String.Compare%2A?displayProperty=fullName> e <xref:System.String.Equals%2A?displayProperty=fullName>, forniscono ora un overload che accetta un valore dell'enumerazione <xref:System.StringComparision?displayProperty=fullName> come parametro.  
  
 Quando si specifica **StringComparison.Ordinal** o **StringComparison.OrdinalIgnoreCase**, il confronto tra stringhe sarà di tipo non linguistico.  In altre parole le funzionalità specifiche del linguaggio naturale vengono escluse dalle decisioni sui confronti.  le quali vengono basate su semplici confronti di byte senza considerare l'utilizzo di maiuscole e minuscole o le tabelle di equivalenza, i cui parametri dipendono dalle impostazioni cultura.  Di conseguenza, l'impostazione esplicita del parametro su **StringComparison.Ordinal** o **StringComparison.OrdinalIgnoreCase** consente spesso di snellire il codice, di aumentarne la correttezza e di renderlo più affidabile.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, impostare il metodo di confronto di stringhe su un overload che accetta l'enumerazione <xref:System.StringComparison?displayProperty=fullName> come parametro e specificare **Ordinal** o **OrdinalIgnoreCase**.  Cambiare ad esempio `String.Compare(str1, str2)` in `String.Compare(str1, str2, StringComparison.Ordinal)`  
  
## Esclusione di avvisi  
 È consigliabile non visualizzare un avviso di questa regola quando la libreria o l'applicazione è destinata a un pubblico locale limitato oppure quando è necessario utilizzare la semantica delle impostazioni cultura correnti.  
  
## Vedere anche  
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)   
 [CA1307: Specificare StringComparison](../code-quality/ca1307-specify-stringcomparison.md)