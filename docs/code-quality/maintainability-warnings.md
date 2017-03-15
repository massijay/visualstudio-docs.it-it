---
title: "Avvisi di manutenibilit&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.maintainabilityrules"
helpviewer_keywords: 
  - "avvisi, manutenibilità"
  - "avvisi dell'analisi codice gestito, avvisi di manutenibilità"
  - "avvisi di manutenibilità"
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Avvisi di manutenibilit&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli avvisi di gestibilità supportano la gestione di librerie e applicazioni.  
  
## In questa sezione  
  
|Regola|Descrizione|  
|------------|-----------------|  
|[CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Un metodo di istanza dichiara un parametro o una variabile locale il cui nome corrisponde a un campo di istanza del tipo dichiarante, pertanto vengono generati errori.|  
|[CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)|Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà.  Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione.|  
|[CA1502: Evitare complessità eccessiva](../code-quality/ca1502-avoid-excessive-complexity.md)|Questa regola misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità di rami condizionali.|  
|[CA1504: Controllare i nomi dei campi fuorvianti](../code-quality/ca1504-review-misleading-field-names.md)|Il nome di un campo di istanza inizia con "s\_" o il nome di un campo statico \(Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) inizia con "m\_".|  
|[CA1505: evitare codice non manutenibile](../code-quality/ca1505-avoid-unmaintainable-code.md)|Un tipo o metodo presenta un valore di indice di gestibilità basso.  Un indice di manutenibilità basso indica che un tipo o un metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione.|  
|[CA1506: Evitare un numero eccessivo di accoppiamenti di classi](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo.|  
  
## Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)