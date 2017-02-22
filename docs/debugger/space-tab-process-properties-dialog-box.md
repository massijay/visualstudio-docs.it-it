---
title: "Scheda Spazio, finestra di dialogo Propriet&#224; processo | Microsoft Docs"
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
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Scheda Spazio, finestra di dialogo Propriet&#224; processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzare la scheda **Spazio** per esaminare lo spazio degli indirizzi di un processo.  Per visualizzare la [finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md), spostare lo stato attivo su una finestra [Visualizzazione processi](../debugger/processes-view.md).  Selezionare un nodo qualsiasi del processo nella struttura ad albero, quindi scegliere **Proprietà** dal menu **Visualizza**.  
  
 Nella scheda **Spazio** sono disponibili le impostazioni seguenti:  
  
|Voce|Descrizione|  
|----------|-----------------|  
|**Show for space marked as**|Utilizzare questa casella di riepilogo per selezionare la categoria di spazio \(immagine, mappato, riservato o non assegnato\).|  
|**Executable Bytes**|Per la categoria selezionata, la somma di tutti gli spazi degli indirizzi utilizzati da questo processo.  La memoria eseguibile è la memoria che può essere eseguita dai programmi, ma può non essere letta o scritta.|  
|**Exec\-Read\-Only Bytes**|Per la categoria selezionata, la somma di tutti gli spazi degli indirizzi in uso con proprietà di sola lettura utilizzati da questo processo.  La memoria eseguibile di sola lettura è la memoria che può essere eseguita e letta.|  
|**Exec\-Read\-Write Bytes**|Per la categoria selezionata, la somma di tutti gli spazi degli indirizzi in uso con proprietà di lettura\/scrittura utilizzati da questo processo.  La memoria di lettura\/scrittura è la memoria che può essere eseguita dai programmi, nonché letta e modificata.|  
|**Exec\-Write Copy Bytes**|Per la categoria selezionata, la somma di tutti gli spazi degli indirizzi che possono essere eseguiti dai programmi, nonché letti e scritti.  Questo tipo di protezione viene utilizzato quando la memoria deve essere condivisa tra processi.  Se per i processi di condivisione è prevista la sola lettura della memoria, verrà utilizzata la stessa memoria.  Se si desidera che un processo di condivisione possa accedere alla scrittura, verrà effettuata una copia di questa memoria per il processo.|  
|**No\-Access Bytes**|Per la categoria selezionata, la somma di tutti gli spazi degli indirizzi che impediscono a un processo di utilizzarli.  Se si tenta di leggere o scrivere viene generata una violazione di accesso.|  
|**Read\-Only Bytes**|Per la categoria selezionata, la somma di tutti gli spazi degli indirizzi che possono essere eseguiti e letti.|  
|**Read\-Write Bytes**|Per la categoria selezionata, la somma di tutti gli spazi degli indirizzi che consentono la lettura e la scrittura.|  
|**Write\-Copy Bytes**|Per la categoria selezionata, la somma di tutti gli spazi degli indirizzi che consentono la condivisione di memoria per la lettura, ma non per la scrittura.  Quando i processi leggono questa memoria, possono condividere la stessa memoria.  Tuttavia, quando un processo di condivisione desidera disporre dell'accesso in lettura\/scrittura a questa memoria condivisa, viene effettuata una copia di tale memoria per la scrittura.|