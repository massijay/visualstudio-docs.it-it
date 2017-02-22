---
title: "Tempo di elaborazione dell&#39;interfaccia utente | Microsoft Docs"
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
  - "vs.cv.threads.timeline.uiprocessing"
helpviewer_keywords: 
  - "Visualizzatore di concorrenze, Tempo di elaborazione dell'interfaccia utente"
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Tempo di elaborazione dell&#39;interfaccia utente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questi segmenti nella sequenza temporale sono associati a tempi di blocco suddivisi in categorie come elaborazione dell'interfaccia utente.  Ciò implica che un thread stia distribuendo messaggi di Windows o eseguendo altre operazioni di interfaccia utente.  In questo periodo un thread è stato bloccato in una API che il visualizzatore di concorrenze calcola come elaborazione dell'interfaccia utente.  Rientrano in questo gruppo le interfacce API `GetMessage()` e `MsgWaitForMultipleObjects()`.  
  
 Se non è identificata alcuna API di blocco predefinita, esaminare gli stack di chiamate e i rapporti di profilo per determinare le cause sottostanti di ritardo.  
  
 La categoria dell'elaborazione di interfaccia utente è importante per comprendere la velocità di risposta delle applicazioni GUI ed è auspicabile in applicazioni basate sulla velocità di risposta dell'Interfaccia utente.  Se ad esempio il thread UI in un'applicazione realizza una durata di elaborazione dell'interfaccia utente del 100%, è probabile che la velocità di risposta del thread sia molto elevata.  Se tuttavia il thread UI trascorre molto tempo su altre categorie, cercarne le cause principali e considerare opzioni per ridurre il numero di categorie non di interfaccia utente nel thread.  
  
## Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)