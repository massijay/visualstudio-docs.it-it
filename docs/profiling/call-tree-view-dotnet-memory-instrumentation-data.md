---
title: "Visualizzazione Struttura ad albero delle chiamate: dati di strumentazione di memoria .NET del profiler | Microsoft Docs"
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
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Struttura ad albero delle chiamate: dati di strumentazione di memoria .NET del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Struttura ad albero delle chiamate dei dati di profilo sull'allocazione di memoria .NET raccolti con il metodo di strumentazione contiene i percorsi di esecuzione della funzione utilizzati nell'applicazione profilata.  La radice della struttura ad albero è il punto di ingresso nell'applicazione o nel componente.  Per ogni nodo della funzione vengono elencate tutte le funzioni chiamate e i dati di intervallo e della memoria .NET relativi alla funzione.  
  
 I valori nella visualizzazione Struttura ad albero delle chiamate sono relativi alle istanze della funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.  I valori percentuali vengono calcolati confrontando il valore delle istanze della funzione rispetto alle dimensioni o al numero totale di allocazioni nell'esecuzione del profilo.  
  
## Evidenziazione del percorso critico di esecuzione  
 Nella visualizzazione Struttura ad albero delle chiamate è possibile espandere ed evidenziare il percorso di esecuzione di una funzione o processo che ha creato la maggior parte degli oggetti di memoria o quelli più grandi.  Per visualizzare il percorso più attivo, fare clic con il pulsante destro del mouse sulla funzione o processo, quindi scegliere **Espandi percorso ricorrente**.  
  
## Impostazione del nodo Radice albero chiamate  
 Ogni processo nell'esecuzione dell'analisi è visualizzato come un nodo radice.  È possibile impostare il nodo iniziale della visualizzazione Struttura ad albero delle chiamate facendo clic con il pulsante destro del mouse sul nodo che si desidera impostare come nodo iniziale e quindi selezionare **Imposta radice**.  
  
 Quando si imposta il nodo radice, si eliminano dalla visualizzazione tutte le altre voci ad eccezione del sottoalbero del nodo selezionato.  È possibile reimpostare il nodo radice sul nodo precedentemente visualizzato; fare clic con il pulsante destro del mouse nella finestra visualizzazione Struttura ad albero delle chiamate e selezionare **Reimposta radice**.  
  
## Generale  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Function Name**|Nome della funzione.|  
|**Function Address**|Indirizzo della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Number of Calls**|Numero totale di chiamate a questa funzione.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Il nome assegnato al processo.|  
|**Time Exclusive Probe Overhead**|Sovraccarico temporale per questa funzione causato dalla strumentazione.  Il sovraccarico per probe è stato sottratto da tutti i tempi esclusivi.|  
|**Time Inclusive Probe Overhead**|Sovraccarico temporale per questa funzione e per le relative funzioni figlio causato dalla strumentazione.  Il sovraccarico per probe è stato sottratto da tutti i tempi inclusivi.|  
|**Type**|Contesto della funzione:<br /><br /> -   **0**: funzione corrente<br />-   **1**: funzione che chiama la funzione corrente<br />-   **2**: funzione chiamata dalla funzione corrente<br /><br /> Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nome funzione radice**|Nome della funzione corrente.  Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valori di memoria .NET  
 I valori di memoria .NET inclusivi di una funzione indicano il numero \(allocazioni\) e le dimensioni \(byte\) di oggetti creati dalla funzione e dalle funzioni chiamate dalla funzione.  
  
 I valori di memoria esclusivi indicano il numero e le dimensioni di oggetti creati dal codice nel corpo nella funzione, ma non dalle funzioni chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Inclusive Allocations**|Numero degli oggetti allocati dalle istanze di questa funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.  Il numero include le allocazioni effettuate dalle funzioni figlio.|  
|**% allocazioni inclusive**|La percentuale di tutti gli oggetti creati durante l'esecuzione della profilatura che rappresentavano allocazioni inclusive delle istanze della funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Exclusive Allocations**|Numero degli oggetti allocati dalle istanze di questa funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.  Non sono incluse le allocazioni effettuate dalle funzioni figlio.|  
|**% allocazioni esclusive**|La percentuale di tutti gli oggetti creati durante l'esecuzione della profilatura che costituivano allocazioni esclusive delle istanze della funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate.|  
  
## Valori inclusivi trascorsi  
 I valori inclusivi trascorsi indicano il tempo trascorso da una funzione nello stack di chiamate.  Sono inclusi il tempo trascorso nelle funzioni chiamate dalla funzione e il tempo trascorso in chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Inclusive Time**|Tempo inclusivo trascorso totale di tutte le chiamate a questa funzione, se effettuate dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Elapsed Inclusive Time %**|Percentuale di tempo inclusivo trascorso totale dell'esecuzione di profilo impiegata nel tempo inclusivo trascorso totale di questa funzione, se chiamata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Tempo inclusivo trascorso medio**|Tempo inclusivo trascorso medio di una chiamata a questa funzione, se effettuata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Tempo inclusivo trascorso massimo**|Tempo inclusivo trascorso massimo di una chiamata a questa funzione, se effettuata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Tempo inclusivo trascorso minimo**|Tempo inclusivo trascorso minimo di una chiamata a questa funzione, se effettuata dalla funzione padre nella struttura ad albero delle chiamate.|  
  
## Valori esclusivi trascorsi  
 I valori esclusivi trascorsi indicano il tempo di esecuzione diretta di una funzione nella parte alta dello stack di chiamate.  È incluso il tempo delle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  Tuttavia, non è incluso il tempo trascorso nelle funzioni chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Exclusive Time**|Tempo esclusivo trascorso totale di tutte le chiamate a questa funzione, se effettuate dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Elapsed Exclusive Time %**|Percentuale di tempo esclusivo trascorso totale dell'esecuzione di profilo impiegata nel tempo esclusivo trascorso totale di questa funzione, se chiamata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Tempo esclusivo trascorso medio**|Tempo esclusivo trascorso medio di una chiamata a questa funzione, se effettuata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Tempo esclusivo trascorso massimo**|Tempo esclusivo trascorso massimo di una chiamata a questa funzione, se effettuata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Tempo esclusivo trascorso minimo**|Tempo esclusivo trascorso minimo di una chiamata a questa funzione, se effettuata dalla funzione padre nella struttura ad albero delle chiamate.|  
  
## Valori inclusivi applicazione  
 I valori inclusivi applicazione indicano il tempo trascorso da una funzione nello stack di chiamate.  Non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  È incluso il tempo trascorso nelle funzioni figlio chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Inclusive Time**|Tempo inclusivo applicazione totale di tutte le chiamate a questa funzione, se effettuate dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Application Inclusive Time %**|Percentuale di tempo inclusivo trascorso totale dell'esecuzione di profilo impiegata nel tempo inclusivo applicazione totale di questa funzione, se chiamata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Tempo inclusivo applicazione medio**|Tempo inclusivo applicazione medio di una chiamata a questa funzione, se effettuata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Tempo inclusivo applicazione massimo**|Tempo inclusivo applicazione massimo di una chiamata a questa funzione, se effettuata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Tempo inclusivo applicazione minimo**|Tempo inclusivo applicazione minimo di una chiamata a questa funzione, se effettuata dalla funzione padre nella struttura ad albero delle chiamate.|  
  
## Valori esclusivi applicazione  
 I valori esclusivi applicazione indicano il tempo trascorso nella funzione, escluso il tempo trascorso nelle funzioni figlio chiamate dalla funzione.  Dal tempo sono inoltre escluse le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Exclusive Time**|Tempo esclusivo applicazione totale di tutte le chiamate a questa funzione, se effettuate dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Application Exclusive Time %**|Percentuale di tempo esclusivo trascorso totale dell'esecuzione di profilo impiegata nel tempo esclusivo dell'applicazione totale di questa funzione, se chiamata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Tempo esclusivo applicazione medio**|Tempo esclusivo applicazione medio di una chiamata a questa funzione, se effettuata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Tempo esclusivo applicazione massimo**|Tempo esclusivo applicazione massimo di una chiamata a questa funzione, se effettuata dalla funzione padre nella struttura ad albero delle chiamate.|  
|**Tempo esclusivo applicazione minimo**|Tempo esclusivo applicazione minimo di una chiamata a questa funzione, se effettuata dalla funzione padre nella struttura ad albero delle chiamate.|