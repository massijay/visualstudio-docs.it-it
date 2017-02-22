---
title: "CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi | Microsoft Docs"
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
  - "VariableNamesShouldNotMatchFieldNames"
  - "CA1500"
helpviewer_keywords: 
  - "VariableNamesShouldNotMatchFieldNames"
  - "CA1500"
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|CheckId|CA1500|  
|Category|Microsoft.Maintainability|  
|Breaking Change|In caso di generazione su un parametro che ha lo stesso nome di un campo:<br /><br /> -   Non sostanziale \- Se il campo e il metodo che dichiara il parametro non sono visibili all'esterno dell'assembly, a prescindere dalle modifiche apportate.<br />-   Sostanziale: se si modifica il nome del campo ed è visibile all'esterno dell'assembly.<br />-   Sostanziale \- Se si modifica il nome del parametro e il metodo che lo dichiara è visibile all'esterno dell'assembly.<br /><br /> In caso di generazione su una variabile locale che ha lo stesso nome di un campo:<br /><br /> -   Non sostanziale: se il campo non è visibile all'esterno dell'assembly, a prescindere dalle modifiche apportate.<br />-   Non sostanziale \- Se si modifica il nome della variabile locale e non si modifica il nome del campo.<br />-   Sostanziale: se si modifica il nome del campo ed è visibile all'esterno dell'assembly.|  
  
## Causa  
 Un metodo di istanza dichiara un parametro o una variabile locale il cui nome corrisponde a un campo di istanza del tipo dichiarante.  Per intercettare le variabili locali che violano la regola, l'assembly testato deve essere compilato con informazioni di debug e il file di database del programma associato \(pdb\) deve essere disponibile.  
  
## Descrizione della regola  
 Quando il nome di un campo di istanza corrisponde a un parametro o a un nome di variabile locale, al campo di istanza si accede utilizzando la parola chiave `this` \(`Me` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) dall'interno del corpo del metodo.  Quando si gestisce il codice, è facile dimenticare tale differenza e presupporre che il parametro o la variabile locale si riferisca a un campo di istanza, generando errori.  in particolare per corpi di metodo di lunga durata.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rinominare il parametro\/la variabile o il campo.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrate due violazioni di questa regola.  
  
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
 [!code-cs[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]