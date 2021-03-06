---
title: "DA0006: Eseguire l&#39;override di Equals() per i tipi di valore | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAOverrideEquals"
  - "vs.performance.6"
  - "vs.performance.DA0006"
  - "vs.performance.rules.DA0006"
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0006: Eseguire l&#39;override di Equals() per i tipi di valore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0006|  
|Categoria|Utilizzo di .NET Framework|  
|Metodi di profilo|Campionamento|  
|Messaggio|Eseguire l'override di Equals e dell'operatore di uguaglianza sui tipi di valore.|  
|Tipo messaggio|Avviso|  
  
## Causa  
 Le chiamate al metodo Equals o agli operatori di uguaglianza di un tipo di valore pubblico rappresentano una percentuale significativa dei dati di profilo.  Considerare l'implementazione di un metodo più efficiente.  
  
## Descrizione della regola  
 Per i tipi di valore, l'implementazione ereditata di Equals utilizza la libreria <xref:System.Reflection> e confronta il contenuto di tutti i campi del tipo.  La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo.  Se si prevede che gli utenti confrontino o ordinino le istanze oppure le utilizzino come chiavi di tabelle hash, il tipo di valore deve implementare Equals.  Se il linguaggio di programmazione in uso supporta l'overload dell'operatore, è necessario fornire un'implementazione degli operatori di uguaglianza e disuguaglianza.  
  
 Per ulteriori informazioni su come eseguire l'overide del metodo Equals e degli operatori di uguaglianza, vedere [Linee guida per l'implementazione del metodo Equals e dell'operatore di uguaglianza](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## Come esaminare un avviso  
 Per un esempio di implementazione degli operatori Equals e di uguaglianza, vedere la regola di analisi del codice [CA1815: Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)