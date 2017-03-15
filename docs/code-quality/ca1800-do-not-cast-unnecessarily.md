---
title: "CA1800: Non eseguire il cast inutilmente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1800"
  - "DoNotCastUnnecessarily"
helpviewer_keywords: 
  - "DoNotCastUnnecessarily"
  - "CA1800"
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1800: Non eseguire il cast inutilmente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotCastUnnecessarily|  
|CheckId|CA1800|  
|Category|Microsoft.Performance|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo esegue cast duplicati su uno dei relativi argomenti o variabili locali.  Affinché venga eseguita un'analisi completa tramite questa regola, l'assembly testato deve essere compilato con informazioni di debug e il file di database del programma associato \(pdb\) deve essere disponibile.  
  
## Descrizione della regola  
 I cast duplicati comportano una riduzione delle prestazioni, in particolare quando i cast vengono eseguiti in istruzioni di iterazione compatte.  Per cast duplicati espliciti, archiviare il risultato del cast in una variabile locale e utilizzare la variabile locale anziché i cast duplicati.  
  
 Se si utilizza l'operatore C\# `is` per verificare l'esito del cast prima che venga effettivamente eseguito, valutare se sia opportuno verificare in alternativa il risultato dell'operatore `as`.  In questo modo viene fornita la stessa funzionalità senza che il cast implicito venga eseguito dall'operatore `is`.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare l'implementazione del metodo per ridurre al minimo il numero di cast.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola, così come dell'intera regola, è sicura se le prestazioni non costituiscono un problema.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un metodo che viola la regola utilizzando l'operatore C\# `is`.  Un secondo metodo soddisfa la regola sostituendo l'operatore `is` con un test sul risultato dell'operatore `as`, il quale riduce il numero di cast per iterazione da due a uno.  
  
 [!code-cs[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati il metodo `start_Click` con più cast espliciti duplicati che viola la regola e un metodo `reset_Click` che soddisfa la regola archiviando il cast in una variabile locale.  
  
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-cs[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]  
  
## Vedere anche  
 [as](/dotnet/csharp/language-reference/keywords/as)   
 [is](/dotnet/csharp/language-reference/keywords/is)