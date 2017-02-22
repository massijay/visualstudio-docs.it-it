---
title: "Scheda Generale, finestra di dialogo Propriet&#224; processo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Proprietà processo per Windows NT"
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Scheda Generale, finestra di dialogo Propriet&#224; processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzare la scheda **Generale** per ottenere ulteriori informazioni su un processo specifico.  Per visualizzare la [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su una finestra [Visualizzazione processi](../debugger/processes-view.md).  Selezionare un nodo qualsiasi del processo nella struttura ad albero, quindi scegliere **Proprietà** dal menu **Visualizza**.  
  
 Nella scheda **Generale** sono disponibili le impostazioni seguenti:  
  
|Voce|Descrizione|  
|----------|-----------------|  
|**Module Name**|Nome del modulo.|  
|**ID processo**|ID univoco di questo processo.  I numeri di ID del processo vengono riutilizzati e pertanto identificano un processo solo per la relativa durata.  Il tipo di oggetto Process viene creato durante l'esecuzione di un programma.  Tutti i thread in un processo condividono lo stesso spazio degli indirizzi e hanno accesso agli stessi dati.|  
|**Priority Base**|Priorità di base corrente del processo.  La priorità di base dei thread all'interno di un processo può aumentare o diminuire in relazione alla priorità di base del processo.|  
|**Thread**|Numero di thread attualmente attivi nel processo.|  
|**CPU Time**|Tempo CPU totale trascorso su questo processo e i relativi thread.  Corrisponde alla somma di User Time e Privileged Time.|  
|**User Time**|Tempo complessivo trascorso impiegato dai thread di questo processo per l'esecuzione di codice in modalità utente in thread attivi.  Le applicazioni vengono eseguite in modalità utente, analogamente a sottosistemi quali la gestione finestre e il motore della grafica.|  
|**Privileged Time**|Tempo totale trascorso per l'esecuzione del processo in modalità privilegiata in thread attivi.  Il livello di servizio, le routine Executive e il kernel vengono eseguiti in modalità privilegiata.  I driver di dispositivo previsti per la maggior parte dei dispositivi escluse le schede grafiche e le stampanti utilizzano parimenti la modalità privilegiata.  Alcune operazioni eseguite da Windows per l'applicazione possono essere incluse in altri processi del sottosistema oltre a Privileged Time.|  
|**Tempo trascorso**|Tempo totale trascorso da quando il processo è in esecuzione.|