---
title: "Visualizzazione Chiamante/chiamato: dati di campionamento del profiler | Microsoft Docs"
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
  - "profilatura del campionamento (metodo), visualizzazione Chiamante/Chiamato"
  - "visualizzazione Chiamante/Chiamato"
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Chiamante/chiamato: dati di campionamento del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Chiamante\/chiamato consente di visualizzare informazioni relative alla profilatura per una funzione selezionata e per le relative funzioni figlio.  Nella visualizzazione Chiamante\/chiamato sono presenti tre griglie.  
  
 **Funzione corrente** viene visualizzato nella griglia al centro e include le informazioni di profilatura per la funzione selezionata.  I valori includono tutte le chiamate campionate alla funzione.  
  
 **Funzioni che hanno chiamato la funzione corrente** viene visualizzato nella griglia superiore e include i singoli contributi delle funzioni computer chiamante \(padre\) ai valori della funzione selezionata \(corrente\).  
  
 **Funzioni che sono state chiamate dalla funzione corrente** viene visualizzato nella griglia inferiore e include le informazioni di profilatura per le funzioni chiamate \(figlio\) della funzione selezionata quando la funzione figlio è stata chiamata dalla funzione corrente.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative in modo che il profiler di Visual Studio consente di raccogliere dati su queste piattaforme.  Le applicazioni di archivio di Windows richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
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
|**Type**|Contesto della funzione:<br /><br /> -   **0** \- funzione corrente<br />-   **1**: funzione che chiama la funzione corrente<br />-   **2**: funzione chiamata dalla funzione corrente|  
|**Nome funzione radice**|Nome della funzione corrente.|  
|**Inclusive Samples**|-   Per la funzione corrente, numero di campioni che sono stati raccolti anche se questa funzione o una delle relative funzioni figlio era in esecuzione.<br />-   Per una funzione computer chiamante, numero di campioni inclusivi della funzione corrente che sono stati raccolti quando questa funzione ha chiamato la funzione corrente.<br />-   Per una funzione computer chiamato, numero di campioni inclusivi di questa funzione che sono stati raccolti quando la funzione corrente ha chiamato questa funzione.|  
|**% campioni inclusivi**|Percentuale di tutti i campioni nell'esecuzione del profilo che costituivano campioni inclusivi di questa funzione.|  
|**Exclusive Samples**|-   Per la funzione corrente, numero di campioni nell'esecuzione del profilo che sono stati raccolti durante l'esecuzione diretta di questa funzione, ovvero quando questa funzione si trovava nella parte alta dello stack di chiamate.  I campioni raccolti durante l'esecuzione delle funzioni figlio di questa funzione non sono inclusi nei conteggi esclusivi.<br />-   Per una funzione computer chiamante, numero di campioni esclusivi della funzione corrente che sono stati raccolti quando questa funzione ha chiamato la funzione corrente.<br />-   Per una funzione computer chiamato, numero di campioni esclusivi di questa funzione che sono stati raccolti quando la funzione corrente ha chiamato questa funzione.|  
|**% campioni esclusivi**|Percentuale di tutti i campioni nell'esecuzione del profilo che costituivano campioni esclusivi di questa funzione.|  
  
## Vedere anche  
 [Visualizzazione Chiamante\/chiamato \- Campionamento](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Chiamante\/chiamato \- Strumentazione](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view-instrumentation-data.md)