---
title: "Scheda Memoria, finestra di dialogo Propriet&#224; processo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Proprietà processo per Windows NT"
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Scheda Memoria, finestra di dialogo Propriet&#224; processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzare la scheda **Memoria** per mostrare il modo in cui un processo utilizza una memoria.  Per visualizzare la [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su una finestra [Visualizzazione processi](../debugger/processes-view.md).  Selezionare un nodo qualsiasi del processo nella struttura ad albero, quindi scegliere **Proprietà** dal menu **Visualizza**.  
  
 Nella scheda **Memoria** sono disponibili le impostazioni seguenti:  
  
|Voce|Descrizione|  
|----------|-----------------|  
|**Byte virtuali**|Dimensioni correnti \(in byte\) dello spazio degli indirizzi virtuali utilizzate dal processo.  L'utilizzo dello spazio degli indirizzi virtuali non implica necessariamente l'utilizzo corrispondente del disco o delle pagine della memoria principale.  Tuttavia, lo spazio virtuale è limitato e un utilizzo eccessivo potrebbe limitare la capacità del processo di caricare le librerie.|  
|**N. massimo byte virtuali**|Numero massimo di byte di spazio degli indirizzi virtuali utilizzato dal processo in qualsiasi momento.|  
|**Working set**|Set di pagine della memoria utilizzate recentemente dai thread nel processo.  Se la memoria libera nel computer supera una soglia, le pagine vengono lasciate nel working set di un processo anche se non sono utilizzate.  Quando la memoria libera scende al di sotto di una soglia, le pagine vengono rimosse dal working set.  Se sono necessarie, verranno riportate come errore software nel working set prima di lasciare la memoria principale.|  
|**Working set massimo**|Numero massimo di pagine nel working set di questo processo in qualsiasi momento.|  
|**Byte riserva di paging**|Quantità corrente di riserva di paging allocata dal processo.  La riserva di paging è un'area della memoria di sistema in cui i componenti del sistema operativo acquisiscono spazio mentre portano a termine le attività definite.  Le pagine della riserva di paging possono essere inviate al file di paging quando il sistema non vi accede per molto tempo.|  
|**Byte riserva non di paging**|Numero corrente di byte nella riserva non di paging allocata dal processo.  La riserva non di paging è un'area della memoria di sistema in cui lo spazio viene acquisito dai componenti del sistema operativo mentre portano a termine le attività definite.  Le pagine della riserva non di paging non possono essere inviate al file di paging; rimangono nella memoria principale finché non vengono allocate.|  
|**Byte privati**|Numero corrente di byte allocato da questo processo che non può essere condiviso con altri processi.|  
|**Byte liberi**|Spazio inutilizzato totale degli indirizzi virtuali di questo processo.|  
|**Byte riservati**|Quantità totale di memoria virtuale riservata per un uso successivo da parte di questo processo.|  
|**Byte immagine liberi**|Quantità di spazio degli indirizzi virtuali che non è utilizzata o riservata dalle immagini all'interno di questo processo.|  
|**Byte immagine riservati**|Somma di tutte le memorie virtuali riservate dalle immagini in esecuzione all'interno di questo processo.|