---
title: "Visualizzazione struttura ad albero delle chiamate: dati su conflitti del profiler | Microsoft Docs"
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
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione struttura ad albero delle chiamate: dati su conflitti del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Albero delle chiamate contiene i percorsi di esecuzione della funzione utilizzati nell'applicazione profilata.  La radice della struttura ad albero è il punto di ingresso nell'applicazione o nel componente.  Ogni nodo di funzione elenca tutte le funzioni chiamate, i numeri di volte in cui è stata bloccata la funzione e la quantità di tempo per cui la funzione è stata bloccata perché si stava contendendo una risorsa con altri thread o processi.  
  
 I valori nella visualizzazione Struttura ad albero delle chiamate sono relativi alle istanze della funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.  I valori percentuali vengono calcolati confrontando il valore delle istanze della funzione al numero totale di conflitti nell'esecuzione del profilo.  
  
## Evidenziazione del percorso critico di esecuzione  
 Nella visualizzazione Struttura ad albero delle chiamate è possibile espandere ed evidenziare il percorso di esecuzione di una funzione o processo che ha creato la maggior parte dei conflitti.  
  
-   Per visualizzare il percorso più attivo, fare clic con il pulsante destro del mouse sulla funzione o processo, quindi scegliere **Espandi percorso ricorrente**.  
  
## Impostazione del nodo Radice albero chiamate  
 Ogni processo nell'esecuzione del profilo è visualizzato come un nodo radice.  Per impostare il nodo iniziale della visualizzazione Struttura ad albero delle chiamate, fare clic con il pulsante destro del mouse sul nodo che si desidera impostare come nodo iniziale, quindi fare clic su **Imposta radice**.  
  
 Quando si imposta il nodo radice, si eliminano dalla visualizzazione tutte le altre voci, ad eccezione del sotto albero del nodo selezionato.  Per reimpostare il nodo radice sul nodo originale, fare clic con il pulsante destro del mouse nella visualizzazione Struttura ad albero delle chiamate, quindi fare clic su **Reimposta radice**.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Tempo blocco esclusivo**|Tempo durante il quale a tali istanze della funzione è stata impedita l'esecuzione durante l'esecuzione del profilo.  Non è incluso il tempo blocco delle funzioni figlio chiamate dalla funzione.|  
|**% tempo blocco esclusivo**|Percentuale del tempo blocco nell'esecuzione del profilo che costituiva il tempo blocco esclusivo per questa funzione in questo percorso di esecuzione.|  
|**Conflitti esclusivi**|Numero di conflitti che si sono verificati nelle istanze della funzione in questo percorso di esecuzione.  Non sono inclusi i conflitti di funzioni figlio chiamate dalla funzione.|  
|**% conflitti esclusivi**|Percentuale di tutti i conflitti nell'esecuzione del profilo che rappresentavano conflitti esclusivi delle istanze di questa funzione chiamati dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Function Address**|Indirizzo della funzione.|  
|**Function Name**|Nome completo della funzione.|  
|**Tempo blocco inclusivo**|Tempo totale durante il quale a tali istanze della funzione è stata impedita l'esecuzione durante l'esecuzione del profilo.  È incluso il tempo blocco delle funzioni figlio chiamate dalla funzione.|  
|**% tempo blocco inclusivo**|Percentuale del tempo blocco nell'esecuzione del profilo che costituiva il tempo blocco inclusivo per le istanze della funzione in questo percorso di esecuzione.|  
|**Conflitti inclusivi**|Numero totale di conflitti che hanno bloccato le istanze della funzione in questo percorso di esecuzione.  Sono inclusi i conflitti di funzioni figlio chiamate dalla funzione.|  
|**% conflitti inclusivi**|Percentuale di tutti i conflitti nell'esecuzione del profilo che costituivano i conflitti inclusivi delle istanze della funzione in questo percorso di esecuzione.|  
|**Livello**|Livello della funzione nella struttura ad albero delle chiamate.  Solo nei rapporti della riga di comando VSReport.  Per ulteriori informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Struttura ad albero delle chiamate](../profiling/call-tree-view.md)   
 [Visualizzazione Struttura ad albero delle chiamate \- Strumentazione](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Struttura ad albero delle chiamate \- Campionamento](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Struttura ad albero delle chiamate](../profiling/call-tree-view-instrumentation-data.md)   
 [Visualizzazione albero delle chiamate](../profiling/call-tree-view-sampling-data.md)