---
title: "Scheda File di paging, finestra di dialogo Propriet&#224; processo | Microsoft Docs"
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
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Scheda File di paging, finestra di dialogo Propriet&#224; processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzare la scheda **File di paging** per esaminare il file di paging di un processo.  Per visualizzare la [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su una finestra [Visualizzazione processi](../debugger/processes-view.md).  Selezionare un nodo qualsiasi del processo nella struttura ad albero, quindi scegliere **Proprietà** dal menu **Visualizza**.  
  
 Nella scheda **File di paging** sono disponibili le impostazioni seguenti:  
  
|Voce|Descrizione|  
|----------|-----------------|  
|**Page File Bytes**|Numero corrente di pagine utilizzate da questo processo nel file di paging.  Il file di paging consente di archiviare le pagine di dati utilizzate dal processo ma non contenute in altri file.  Il file di paging viene utilizzato da tutti i processi e la mancanza di spazio nel file di paging può causare errori mentre gli altri processi sono in esecuzione.|  
|**Peak Page File Bytes**|Numero massimo di pagine utilizzate da questo processo nel file di paging.|  
|**Page Faults**|Numero di errori di pagina relativi ai thread eseguiti in questo processo.  Un errore di pagina si verifica quando un thread fa riferimento a una pagina della memoria virtuale che non è presente nel working set nella memoria principale.  Pertanto, la pagina non sarà recuperata dal disco se si trova nell'elenco standby e quindi già nella memoria principale o se viene utilizzata da un altro processo con il quale è condivisa.|