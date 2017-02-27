---
title: "Rapporto marcatori | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.markers"
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Rapporto marcatori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il Rapporto Marcatori elenca i marcatori nel calendario visualizzato.  La panoramica o lo zoom, o le corsie nascoste, potrebbero far comparire o scomparire marcatori.  Il rapporto contiene le informazioni su ogni marcatore:  
  
-   Il tempo in cui è stata avviata, relativo all'inizio della traccia.  
  
-   La durata.  La durata è zero per i flag e i messaggi poiché rappresentano un istante.  
  
-   L'ID del thread che lo ha generato.  
  
-   La Gestione Eventi per il provider di Windows \(ETW\) che l'ha generata.  
  
-   La serie di marcatori da cui è stato scritto.  
  
-   La categoria di eventi a cui appartiene.  
  
-   Il livello di importanza.  
  
-   Il tipo \(intervallo, flag, o messaggio\).  
  
-   Descrizione dettagliata di cosa rappresenta  
  
 Scegliere il pulsante **Esporta** per salvare il Rapporto Marcatori come file CSV.  È possibile utilizzare i dati nel file CSV con altre applicazioni o strumenti.  
  
> [!NOTE]
>  Il Rapporto Marcatori può visualizzare 1.000 marcatori.  Per visualizzare tutti i marcatori, esportare il rapporto completo su un file CSV.