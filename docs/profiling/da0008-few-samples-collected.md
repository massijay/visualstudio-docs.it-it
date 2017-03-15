---
title: "DA0008: Numero ridotto di campioni raccolti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DATooFewSamples"
  - "vs.performance.8"
  - "vs.performance.DA0008"
  - "vs.performance.rules.DA0008"
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# DA0008: Numero ridotto di campioni raccolti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0008|  
|Category|Utilizzo di strumenti di profilatura|  
|Metodo di profilatura|Campionamento|  
|Messaggio|Sono stati raccolti solo alcuni campioni.  Considerare un'esecuzione più lunga o una frequenza di campionamento più veloce per ottenere risultati più significativi.|  
|Tipo regola|Informazioni|  
  
## Causa  
 Solo alcuni campioni sono stati raccolti nell'esecuzione del profilo.  
  
## Descrizione della regola  
 Quando viene utilizzato il metodo di campionamento, è necessario raccogliere un numero di campioni statisticamente significativo per assicurarsi che i dati siano rappresentativi dell'effettivo comportamento del programma.  Per ridurre al minimo gli errori di campionamento, provare a raccogliere almeno 1000 campioni di comportamento dell'esecuzione delle istruzioni del programma.  Se non si raccoglie un numero sufficiente di campioni è possibile che l'analisi dei dati di profilo porti a conclusioni fuorvianti.  
  
## Come correggere le violazioni  
 Considerare la possibilità di profilare un'esecuzione più lunga dell'applicazione o di utilizzare una frequenza di campionamento più elevata per ottenere risultati significativi a livello statistico.  Per informazioni su come modificare la frequenza di campionamento nell'IDE di Visual Studio, consultare [Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md).  Per ulteriori informazioni sulla modifica della frequenza di campionamento quando si utilizza la riga di comando degli strumenti di profilo, vedere [Timer](../profiling/timer.md) nelle informazioni di riferimento di [VSPerfCmd](../profiling/vsperfcmd.md).