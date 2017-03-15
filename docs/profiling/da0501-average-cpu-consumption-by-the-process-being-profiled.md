---
title: "DA0501: Consumo medio CPU del processo sottoposto a profilatura. | Microsoft Docs"
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
  - "vs.performance.rules.DA0501"
  - "vs.performance.DA0501"
  - "vs.performance.501"
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0501: Consumo medio CPU del processo sottoposto a profilatura.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA501|  
|Category|Monitoraggio risorse|  
|Metodo di profilatura|Tutte|  
|Messaggio|Consumo medio CPU del processo sottoposto a profilatura.|  
|Tipo regola|Informazioni|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## Descrizione della regola  
 In questo messaggio viene indicata la percentuale di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione.  Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo profilato era attivo.  Il valore può essere maggiore di 100% su un computer con più di un processore.  
  
## Come utilizzare i dati della regola  
 Utilizzare il valore della regola per confrontare le prestazioni di versioni o compilazioni diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di test diversi.