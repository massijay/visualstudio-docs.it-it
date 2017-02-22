---
title: "Visualizzazione Righe: dati su conflitti del profiler | Microsoft Docs"
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
  - "Righe (visualizzazione)"
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Righe: dati su conflitti del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Righe dei dati di conflitto sono elencati i dati delle prestazioni per le istruzioni in esecuzione durante la raccolta dei campioni nell'esecuzione del profilo.  In un file di origine un'istruzione può occupare più di una riga e una singola riga può includere più di un'istruzione.  
  
 Un'istruzione viene identificata dai dati seguenti:  
  
-   File di origine che contiene l'istruzione della funzione.  
  
-   Funzione che contiene l'istruzione.  
  
-   Riga di codice sorgente in cui inizia l'istruzione.  
  
-   Carattere nella riga di codice sorgente in corrispondenza del quale inizia l'istruzione.  
  
-   Riga di codice sorgente in cui termina l'istruzione.  
  
-   Carattere nella riga di codice sorgente in corrispondenza del quale termina l'istruzione.  
  
 Nella colonna Nome riga viene fornita una concatenazione ordinabile dei dati dell'identificatore.  
  
 Nella tabella seguente vengono descritte le colonne del rapporto Visualizzazione Righe.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Tempo blocco esclusivo**|Quantità di tempo durante la quale è stata impedita l'esecuzione del codice nell'istruzione a causa di un evento di conflitto.  Non è incluso il tempo blocco nelle funzioni chiamate dall'istruzione.|  
|**% tempo blocco esclusivo**|Percentuale del tempo blocco nel processo che costituiva il tempo blocco esclusivo dell'istruzione.|  
|**Conflitti esclusivi**|Numero di volte in cui è stata impedita l'esecuzione del codice nell'istruzione a causa di un evento di conflitto.  Non sono inclusi gli eventi di conflitto nelle funzioni chiamate dalla funzione.|  
|**% conflitti esclusivi**|Percentuale di tutti gli eventi di conflitto nel processo che costituivano conflitti esclusivi di questa istruzione.|  
|**Function Address**|Indirizzo della funzione che contiene questa istruzione.|  
|**Function Name**|Nome completo della funzione che contiene questa istruzione.|  
|**Tempo blocco inclusivo**|Tempo blocco in questa istruzione e nelle funzioni chiamate nell'istruzione.|  
|**% tempo blocco inclusivo**|Percentuale del tempo blocco nel processo che costituiva il tempo blocco inclusivo dell'istruzione.|  
|**Conflitti inclusivi**|Numero di volte in cui è stata impedita l'esecuzione di questa istruzione e delle funzioni chiamate nell'istruzione.|  
|**% conflitti inclusivi**|Percentuale di tutti gli eventi di conflitto nel processo che costituivano conflitti inclusivi di questa istruzione.|  
|**Nome riga**|Identificatore generato dal profiler della riga.  L'identificatore utilizza la sintassi seguente:`SourceFile`**;\[**`LineNumberStart`**,**`CharacterStart`**\]\-\>;\[**`LineNumberEnd`**,**`CharacterEnd`**\]**|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Module Name**|Nome del modulo che contiene l'istruzione.|  
|**Percorso modulo**|Percorso del modulo che contiene l'istruzione.|  
|**ID processo**|ID del processo profilato.|  
|**Nome di processo**|Nome del processo.|  
|**Inizio origine del carattere**|Offset del carattere iniziale nella riga del file di origine da cui inizia questa istruzione.|  
|**Fine origine del carattere**|Offset del carattere iniziale nella riga del file di origine da cui termina questa istruzione.|  
|**File di origine**|Nome del file di origine che contiene l'istruzione della funzione.|  
|**Inizio della riga di codice sorgente**|Numero di riga nel file di origine in corrispondenza del quale inizia l'istruzione.|  
|**Fine della riga di codice sorgente**|Numero di riga nel file di origine in corrispondenza del quale termina l'istruzione.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Righe](../profiling/lines-view.md)   
 [Visualizzazione Righe \- Campionamento](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Righe](../profiling/lines-view-sampling-data.md)