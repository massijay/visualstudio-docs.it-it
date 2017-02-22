---
title: "CA1501: Evitare ereditariet&#224; eccessiva | Microsoft Docs"
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
  - "CA1501"
  - "AvoidExcessiveInheritance"
helpviewer_keywords: 
  - "AvoidExcessiveInheritance"
  - "CA1501"
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1501: Evitare ereditariet&#224; eccessiva
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|Category|Microsoft.Maintainability|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà.  
  
## Descrizione della regola  
 Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione.  Questa regola limita l'analisi alle gerarchie che si trovano all'interno dello stesso modulo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, derivare il tipo da un tipo di base meno annidato nella gerarchia di ereditarietà o eliminare alcuni dei tipi di base intermedi.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura.  Tuttavia, il codice potrebbe essere più difficile da gestire.  Si noti che, in base alla visibilità dei tipi di base, la risoluzione delle violazioni di questa regola potrebbe determinare modifiche importanti.  La rimozione dei tipi di base pubblici, ad esempio, è una modifica importante.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola la regola.  
  
 [!code-cs[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]