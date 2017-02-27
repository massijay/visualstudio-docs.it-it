---
title: "CA1815: Eseguire l&#39;override di Equals e dell&#39;operatore &quot;uguale a&quot; sui tipi di valore | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1815"
  - "OverrideEqualsAndOperatorEqualsOnValueTypes"
helpviewer_keywords: 
  - "OverrideEqualsAndOperatorEqualsOnValueTypes"
  - "CA1815"
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1815: Eseguire l&#39;override di Equals e dell&#39;operatore &quot;uguale a&quot; sui tipi di valore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|CheckId|CA1815|  
|Category|Microsoft.Performance|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo di valore pubblico non esegue l'override di <xref:System.Object.Equals%2A?displayProperty=fullName> o non implementa l'operatore di uguaglianza \(\=\=\).  Questa regola non richiede il controllo delle enumerazioni.  
  
## Descrizione della regola  
 Per i tipi di valore, l'implementazione ereditata di <xref:System.Object.Equals%2A> utilizza la libreria Reflection e confronta il contenuto di tutti i campi.  La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo.  Se si prevede che gli utenti confrontino o ordinino le istanze oppure le utilizzino come chiavi di tabelle hash, il tipo di valore deve implementare <xref:System.Object.Equals%2A>.  Se il linguaggio di programmazione in uso supporta l'overload dell'operatore, è necessario fornire un'implementazione degli operatori di uguaglianza e disuguaglianza.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, fornire un'implementazione di <xref:System.Object.Equals%2A>.  Se possibile, implementare l'operatore di uguaglianza.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se le istanze del tipo di valore non verranno confrontate tra loro.  
  
## Esempio di una violazione  
  
### Descrizione  
 Nell'esempio riportato di seguito viene mostrata una struttura \(tipo di valore\) che viola questa regola.  
  
### Codice  
 [!code-cs[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## Esempio di correzione  
  
### Descrizione  
 Nell'esempio seguente viene corretta la violazione precedente eseguendo l'override di <xref:System.ValueType.Equals%2A?displayProperty=fullName> e implementando gli operatori di uguaglianza \(\=\=\! \=\).  
  
### Codice  
 [!code-cs[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## Regole correlate  
 [CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## Vedere anche  
 <xref:System.Object.Equals%2A?displayProperty=fullName>