---
title: "Visualizzazione Struttura ad albero delle chiamate: dati di campionamento di memoria .NET del profiler | Microsoft Docs"
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
  - "visualizzazione Struttura ad albero delle chiamate"
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Struttura ad albero delle chiamate: dati di campionamento di memoria .NET del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Albero delle chiamate contiene i percorsi di esecuzione della funzione utilizzati nell'applicazione profilata.  La radice della struttura ad albero è il punto di ingresso nell'applicazione o nel componente.  Per ogni nodo della funzione vengono elencate tutte le funzioni chiamate e i dati sull'allocazione di memoria .NET delle relative chiamate di funzione.  
  
 I valori nella visualizzazione Struttura ad albero delle chiamate sono relativi alle istanze della funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.  I valori percentuali vengono calcolati confrontando il valore delle istanze della funzione rispetto alle dimensioni o al numero totale di allocazioni nell'esecuzione del profilo.  
  
## Evidenziazione del percorso critico di esecuzione  
 Nella visualizzazione Struttura ad albero delle chiamate è possibile espandere ed evidenziare il percorso di esecuzione di una funzione o processo che ha creato la maggior parte degli oggetti di memoria o quelli più grandi.  Per visualizzare il percorso più attivo, fare clic con il pulsante destro del mouse sulla funzione o processo, quindi scegliere **Espandi percorso ricorrente**.  
  
## Impostazione del nodo Radice albero chiamate  
 Ogni processo nell'esecuzione dell'analisi è visualizzato come un nodo radice.  Per impostare il nodo iniziale della visualizzazione Struttura ad albero delle chiamate su un altro nodo, fare clic con il pulsante destro del mouse sul nodo che si desidera impostare come nodo iniziale e selezionare **Imposta radice**.  
  
 Quando si imposta il nodo radice, si eliminano dalla visualizzazione tutte le altre voci ad eccezione del sottoalbero del nodo selezionato.  È possibile reimpostare il nodo radice sul nodo precedentemente visualizzato; fare clic con il pulsante destro del mouse nella finestra visualizzazione Struttura ad albero delle chiamate e selezionare **Reimposta radice**.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Function Name**|Nome completo della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Function Address**|Indirizzo della funzione.|  
|**Livello**|Profondità della funzione nella struttura ad albero delle chiamate.|  
|**Inclusive Allocations**|Numero degli oggetti allocati dalle istanze di questa funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.  Il numero include le allocazioni effettuate dalle funzioni figlio.|  
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che costituivano allocazioni inclusive di questa funzione.|  
|**Exclusive Allocations**|Numero degli oggetti allocati dalle istanze di questa funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.  Non sono incluse le allocazioni effettuate dalle funzioni figlio.|  
|**% allocazioni esclusive**|La percentuale di tutti gli oggetti creati durante l'esecuzione della profilatura che costituivano allocazioni esclusive delle istanze della funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Byte inclusivi**|Numero dei byte in memoria allocati dalle istanze della funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.  Il numero include le allocazioni effettuate dalle funzioni figlio.|  
|**% byte inclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che costituivano allocazioni inclusive di questa funzione.|  
|**Byte esclusivi**|Numero dei byte in memoria allocati dalle istanze della funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.  Non sono incluse le allocazioni effettuate dalle funzioni figlio.|  
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che costituivano allocazioni esclusive di questa funzione.|  
  
## Vedere anche  
 [Visualizzazione Struttura ad albero delle chiamate \- Strumentazione](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione albero delle chiamate](../profiling/call-tree-view-sampling-data.md)   
 [Visualizzazione Struttura ad albero delle chiamate](../profiling/call-tree-view-instrumentation-data.md)