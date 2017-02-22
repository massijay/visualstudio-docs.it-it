---
title: "Visualizzazione albero delle chiamate: dati di campionamento del profiler | Microsoft Docs"
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
  - "profilatura del campionamento (metodo), visualizzazione albero delle chiamate"
  - "albero delle chiamate, visualizzazione"
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione albero delle chiamate: dati di campionamento del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Albero delle chiamate contiene i percorsi di esecuzione della funzione utilizzati nell'applicazione profilata.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative in modo che il profiler di Visual Studio consente di raccogliere dati su queste piattaforme.  Le applicazioni di archivio di Windows richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 La radice della struttura ad albero è il punto di ingresso nell'applicazione o nel componente.  Per ogni nodo della funzione vengono elencate tutte le funzioni chiamate e i dati delle prestazioni delle relative chiamate di funzione.  
  
 I valori nella visualizzazione Struttura ad albero delle chiamate sono relativi alle istanze della funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.  I valori percentuali vengono calcolati confrontando il valore delle istanze della funzione al numero totale di campioni nell'esecuzione del profilo.  
  
## Evidenziazione del percorso critico di esecuzione  
 Nella visualizzazione Struttura ad albero delle chiamate è possibile espandere ed evidenziare il percorso di esecuzione di una funzione o processo con la frequenza di campionamento più elevata.  Per visualizzare il percorso più attivo, fare clic con il pulsante destro del mouse sulla funzione o processo, quindi scegliere **Espandi percorso ricorrente**.  
  
## Impostazione del nodo Radice albero chiamate  
 Ogni processo nell'esecuzione dell'analisi è visualizzato come un nodo radice.  Per impostare il nodo iniziale della visualizzazione Struttura ad albero delle chiamate, fare clic con il pulsante destro del mouse sul nodo che si desidera impostare come nodo iniziale e selezionare **Imposta radice**.  
  
 Quando si imposta il nodo radice, si eliminano dalla visualizzazione tutte le altre voci ad eccezione del sottoalbero del nodo selezionato.  Per reimpostare il nodo radice sul nodo originale, fare clic con il pulsante destro del mouse nella visualizzazione Struttura ad albero delle chiamate e selezionare **Reimposta radice**.  
  
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
|**Livello**|Profondità di questa funzione nella struttura ad albero delle chiamate.  Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Exclusive Samples**|Numero di campioni raccolti in questa funzione quando è stata chiamata dalla funzione padre nella struttura ad albero delle chiamate.  Non sono inclusi i campioni raccolti nelle funzioni chiamate dalla funzione.|  
|**% campioni esclusivi**|La percentuale di tutti i campioni creati durante l'esecuzione del profilo che costituivano campioni esclusivi di questa funzione quando è stata chiamata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Inclusive Samples**|Numero di campioni raccolti in questa funzione quando è stata chiamata dalla funzione padre nella struttura ad albero delle chiamate.  Sono inclusi i campioni raccolti nelle funzioni chiamate dalla funzione.|  
|**% campioni inclusivi**|Percentuale di tutti i campioni durante l'esecuzione del profilo che costituivano campioni inclusivi di questa funzione quando è stata chiamata dalla funzione padre nella struttura ad albero delle chiamate.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Call Tree View \- Profiler Sampling Data](../profiling/call-tree-view-sampling-data.md)   
 [Visualizzazione Struttura ad albero delle chiamate \- Campionamento](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Struttura ad albero delle chiamate \- Strumentazione](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Struttura ad albero delle chiamate](../profiling/call-tree-view-instrumentation-data.md)