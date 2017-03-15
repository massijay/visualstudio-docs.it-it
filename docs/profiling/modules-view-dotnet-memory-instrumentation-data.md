---
title: "Visualizzazione Moduli: dati di strumentazione di memoria .NET del profiler | Microsoft Docs"
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
  - "visualizzazione Moduli"
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Moduli: dati di strumentazione di memoria .NET del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Moduli dei dati di allocazione di memoria .NET raccolti con il metodo di strumentazione raggruppa i dati di memoria e intervallo in base ai moduli eseguiti nell'esecuzione della profilatura.  I dati di profilo per le funzioni del modulo sono elencati nel nodo modulo.  
  
## Generale  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome della funzione o del modulo.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Number of Calls**|Numero totale di chiamate effettuate alla funzione o al modulo.|  
|**File di origine**|File di origine che contiene la definizione di questa funzione.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo in cui è in esecuzione il modulo o la funzione.|  
|**Time Exclusive Probe Overhead**|Sovraccarico temporale per questa funzione o modulo causato dalla strumentazione.|  
|**Time Inclusive Probe Overhead**|Sovraccarico temporale per questa funzione o modulo e relative funzioni figlio causato dalla strumentazione.|  
  
## Valori di memoria .NET  
 I valori di memoria .NET inclusivi di una funzione indicano il numero \(allocazioni\) e le dimensioni \(byte\) di oggetti creati dalla funzione e dalle relative funzioni figlio.  
  
 I valori di memoria esclusivi indicano il numero e le dimensioni di oggetti creati dalla funzione, ma non dalle relative funzioni figlio.  
  
 I valori di memoria inclusivi ed esclusivi di un modulo rappresentano la somma dei valori di memoria inclusivi ed esclusivi delle funzioni nel modulo.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Inclusive Allocations**|-   Per una funzione, numero totale di oggetti creati dalla funzione.  Il numero include gli oggetti creati dalle funzioni chiamate dalla funzione.<br />-   Per un modulo, il numero di oggetti in un'esecuzione del profilo che sono stati allocati quando era in esecuzione almeno una funzione del modulo.  Sono inclusi gli oggetti allocati nelle funzioni generate da chiamate provenienti dalle funzioni del modulo.|  
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti allocati nell'esecuzione della profilatura che costituivano allocazioni inclusive del modulo o della funzione.|  
|**Exclusive Allocations**|-   Per una funzione, numero di oggetti creati durante l'esecuzione di codice nel corpo della funzione \(ovvero quando la funzione si trovava nella parte alta dello stack di chiamate\).  Non sono inclusi gli oggetti creati in funzioni chiamate dalla funzione.<br />-   Per un modulo, somma delle allocazioni esclusive delle funzioni nel modulo.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti allocati nell'esecuzione della profilatura che costituivano allocazioni esclusive del modulo o della funzione.|  
|**Byte esclusivi**|-   Per una funzione, il numero totale di byte di memoria allocati durante l'esecuzione di codice nel corpo della funzione \(ovvero quando la funzione si trovava nella parte alta dello stack di chiamate\).  Non sono inclusi i byte allocati nelle funzioni chiamate dalla funzione.<br />-   Per un modulo, somma dei byte esclusivi allocati dalle funzioni nel modulo.|  
|**% byte esclusivi**|Percentuale di tutti i byte allocati nell'esecuzione della profilatura che rappresentavano byte esclusivi del modulo, della funzione, della riga o dell'istruzione.|  
|**Byte inclusivi**|-   Per una funzione, il numero di byte allocati dalla funzione.  Sono inclusi i byte allocati nelle funzioni chiamate dalla funzione.<br />-   Per un modulo, il numero di byte allocati in un'esecuzione del profilo che sono stati allocati quando era in esecuzione almeno una funzione del modulo.  Sono inclusi gli oggetti creati in tutte le funzioni chiamate dalle funzioni del modulo.|  
|**% byte inclusivi**|Percentuale di tutti i byte allocati nell'esecuzione della profilatura che rappresentavano byte inclusivi del modulo o della funzione.|  
  
## Valori inclusivi trascorsi  
 I valori inclusivi trascorsi indicano il tempo trascorso da una funzione nello stack di chiamate.  È incluso il tempo trascorso nelle funzioni figlio e nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Inclusive Time**|-   Per una funzione, il tempo trascorso nella funzione.  È incluso il tempo trascorso nelle funzioni figlio e nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per un modulo, il periodo di tempo in cui almeno una funzione del modulo si trovava nello stack di chiamate.|  
|**Elapsed Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo trascorso totale del modulo o funzione.|  
|**Tempo inclusivo trascorso medio**|-   Per una funzione, il tempo inclusivo trascorso medio di una chiamata a questa funzione.<br />-   Per un modulo, il tempo inclusivo trascorso medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo trascorso massimo**|-   Per una funzione, il tempo inclusivo trascorso massimo di una chiamata a questa funzione.<br />-   Per un modulo, il tempo inclusivo trascorso massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo trascorso minimo**|-   Per una funzione, il tempo inclusivo trascorso minimo di una chiamata al modulo o alla funzione.<br />-   Per un modulo, il tempo inclusivo trascorso minimo di tutte le chiamate a funzioni nel modulo.|  
  
## Valori esclusivi trascorsi  
 I valori esclusivi trascorsi indicano il tempo di esecuzione diretta di una funzione nella parte alta dello stack di chiamate.  È incluso il tempo nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma non è incluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Exclusive Time**|-   Per una funzione, il tempo trascorso nel modulo o nella funzione.  È escluso il tempo trascorso nelle funzioni figlio, ma sono incluse le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per un modulo, somma dei tempi esclusivi trascorsi delle funzioni nel modulo.|  
|**Elapsed Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo trascorso totale di questo modulo o funzione.|  
|**Tempo esclusivo trascorso medio**|-   Per una funzione, il tempo esclusivo trascorso medio di una chiamata a questa funzione.<br />-   Per un modulo, il tempo esclusivo trascorso medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo trascorso massimo**|-   Per una funzione, il tempo esclusivo trascorso massimo di una chiamata a questa funzione.<br />-   Per un modulo, il tempo esclusivo trascorso massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo trascorso minimo**|-   Per una funzione, il tempo esclusivo trascorso minimo di una chiamata al modulo o alla funzione.<br />-   Per un modulo, il tempo esclusivo trascorso minimo di tutte le chiamate a funzioni nel modulo.|  
  
## Valori inclusivi applicazione  
 I valori inclusivi applicazione indicano il tempo trascorso da una funzione nello stack di chiamate.  Non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma è incluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Inclusive Time**|-   Per una funzione, il tempo trascorso per le chiamate alla funzione.  È incluso il tempo trascorso nelle funzioni figlio, ma sono escluse le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per un modulo, il periodo di tempo in cui almeno una funzione del modulo si trovava nello stack di chiamate, escluso il tempo trascorso nelle chiamate al sistema operativo.|  
|**Application Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo applicazione di questo modulo o funzione.|  
|**Tempo inclusivo applicazione medio**|-   Per una funzione, il tempo inclusivo applicazione medio di una chiamata a questa funzione.<br />-   Per un modulo, il tempo inclusivo applicazione medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo applicazione massimo**|-   Per una funzione, il tempo inclusivo applicazione massimo di una chiamata a questa funzione.<br />-   Per un modulo, il tempo inclusivo applicazione massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo applicazione minimo**|-   Per una funzione, il tempo inclusivo applicazione minimo di una chiamata al modulo o alla funzione.<br />-   Per un modulo, il tempo inclusivo applicazione minimo di tutte le chiamate a funzioni nel modulo.|  
  
## Valori esclusivi applicazione  
 I valori esclusivi applicazione indicano il tempo trascorso nel modulo o nella funzione, escluso il tempo trascorso nelle funzioni figlio.  Dal tempo indicato sono inoltre escluse le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Exclusive Time**|-   Per una funzione, il tempo esclusivo applicazione totale di chiamate a questa funzione.<br />-   Per un modulo, il tempo esclusivo applicazione totale di tutte le chiamate a funzioni nel modulo.|  
|**Application Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo applicazione di questo modulo o funzione.|  
|**Tempo esclusivo applicazione medio**|-   Per una funzione, il tempo esclusivo applicazione medio di una chiamata a questa funzione.<br />-   Per un modulo, il tempo esclusivo applicazione medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo applicazione massimo**|-   Per una funzione, il tempo esclusivo applicazione massimo di una chiamata a questa funzione.<br />-   Per un modulo, il tempo esclusivo applicazione massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo applicazione minimo**|-   Per una funzione, il tempo esclusivo applicazione minimo di una chiamata al modulo o alla funzione.<br />-   Per un modulo, il tempo esclusivo applicazione minimo di tutte le chiamate a funzioni nel modulo.|  
  
## Vedere anche  
 [Visualizzazione Moduli \- Campionamento](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Moduli](../profiling/modules-view-instrumentation-data.md)   
 [Visualizzazione Moduli](../profiling/modules-view-sampling-data.md)