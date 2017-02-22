---
title: "DA0502: Consumo massimo CPU del processo sottoposto a profilatura | Microsoft Docs"
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
  - "vs.performance.rules.DA0502"
  - "vs.performance.DA0502"
  - "vs.performance.502"
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0502: Consumo massimo CPU del processo sottoposto a profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0502|  
|Category|Monitoraggio risorse|  
|Metodo di profilatura|Tutte|  
|Messaggio|Regola a solo scopo informativo.  Il contatore di tempo processore Process\(\)\\\\% misura il consumo di CPU del processo sottoposto a profilatura.  Il valore restituito corrisponde al valore massimo osservato per tutti gli intervalli di misurazione.|  
|Tipo regola|Informativa|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## Descrizione della regola  
 In questo messaggio viene indicata la percentuale massima di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione.  Il valore indicato è il valore massimo segnalato fra tutti gli intervalli di misurazione nei quali il processo profilato era attivo.  La percentuale può essere maggiore di 100% su un computer con più di un processore.  
  
## Come utilizzare i dati della regola  
 Utilizzare il valore della regola per confrontare le prestazioni di versioni o compilazioni diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di profilatura diversi.