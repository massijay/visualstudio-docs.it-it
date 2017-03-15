---
title: "DA0013: Utilizzo elevato di String.Split/String.Substring | Microsoft Docs"
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
  - "vs.performance.13"
  - "vs.performance.rules.DAAvoidStringSubstr"
  - "vs.performance.DA0013"
  - "vs.performance.rules.DA0013"
helpviewer_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DA0013"
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0013: Utilizzo elevato di String.Split/String.Substring
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0013|  
|Category|Guida all'utilizzo di .NET Framework|  
|Metodi di profilatura|Campionamento|  
|Messaggio|Si consiglia di ridurre l'utilizzo delle funzioni String.Split e String.Substring.|  
|Tipo regola|Avviso|  
  
## Causa  
 Le chiamate ai metodi System.String.Split o System.String.Substring rappresentano una percentuale significativa dei dati di profilo.  Considerare l'utilizzo di System.String.IndexOf o System.String.IndexOfAny se si sta verificando l'esistenza di una sottostringa in una stringa.  
  
## Descrizione della regola  
 Il metodo Split agisce su un oggetto stringa e restituisce una nuova matrice di stringhe che contiene le sottostringhe dell'originale.  La funzione alloca memoria per l'oggetto matrice restituito e alloca un nuovo oggetto String per ogni elemento della matrice che trova.  Allo stesso modo, il metodo Substr funziona su un oggetto String e restituisce una nuova stringa equivalente alla sottostringa richiesta.  
  
 Se la gestione delle allocazioni di memoria è di importanza fondamentale nell'applicazione è consigliabile utilizzare alternative ai metodi String.Split e String.Substr.  Ad esempio, è possibile utilizzare il metodo IndexOf o IndexOfAny per individuare una sottostringa specifica all'interno di una String di caratteri senza creare una nuova istanza della classe String.  
  
## Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare a [Visualizzazione Dettagli funzione](../profiling/function-details-view.md) dei dati di profilo di campionamento.  Esaminare le funzioni chiamanti per trovare le sezioni del programma che fanno maggior uso dei metodi System.String.Split o System.String.Substr.  Se è possibile, utilizzare il metodo IndexOf o IndexOfAny per individuare una sottostringa specifica all'interno di una String di caratteri senza creare una nuova istanza della classe String.