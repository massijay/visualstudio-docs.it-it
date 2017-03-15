---
title: "Visualizzazione Righe: dati di campionamento di memoria .NET del profiler | Microsoft Docs"
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
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Righe: dati di campionamento di memoria .NET del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Righe dei dati di profilatura sull'allocazione di memoria .NET che utilizza il metodo di campionamento vengono elencate le istruzioni che hanno allocato la memoria durante l'esecuzione della profilatura.  Nelle colonne vengono inoltre inclusi la dimensione e il numero delle allocazioni.  
  
 In un file di origine un'istruzione può occupare più di una riga e una singola riga può includere più di un'istruzione.  
  
 Un'istruzione viene identificata da quanto segue:  
  
-   File di origine che contiene l'istruzione della funzione.  
  
-   Funzione che contiene l'istruzione.  
  
-   Riga di codice sorgente in cui inizia l'istruzione.  
  
-   Carattere nella riga di codice sorgente in corrispondenza del quale inizia l'istruzione.  
  
-   Riga di codice sorgente in cui termina l'istruzione.  
  
-   Carattere nella riga di codice sorgente in corrispondenza del quale termina l'istruzione.  
  
 Nella colonna Nome riga viene fornita una concatenazione ordinabile dei dati dell'identificatore.  
  
 Per definizione, un'istruzione non chiama altre funzioni.  Di conseguenza, vengono elencati solo i valori esclusivi.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**ID processo**|ID processo dell'esecuzione del profilo.|  
|**Nome di processo**|Nome del processo.|  
|**Module Name**|Nome del modulo che contiene l'istruzione.|  
|**Percorso modulo**|Percorso del modulo che contiene l'istruzione.|  
|**File di origine**|File di origine che contiene l'istruzione.|  
|**Function Name**|Nome della funzione che contiene l'istruzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Function Address**|Indirizzo iniziale della funzione.|  
|**Inizio della riga di codice sorgente**|Numero di riga iniziale nel file di origine in corrispondenza del quale si è verificata l'allocazione.|  
|**Fine della riga di codice sorgente**|Numero di riga finale nel file di origine in corrispondenza del quale si è verificata l'allocazione.|  
|**Inizio origine del carattere**|Offset del carattere iniziale nella riga del file di origine in corrispondenza del quale si è verificata l'allocazione.|  
|**Fine origine del carattere**|Offset del carattere finale nella riga del file di origine in corrispondenza del quale si è verificata l'allocazione.|  
|**Nome riga**|Identificatore generato dal profiler della riga con la sintassi seguente:`Source File`**;\[**`Line Number Start`**,**`Character Start`**\]\-\>;\[**`Line Number Start,Character Start`**\]**|  
|**Exclusive Allocations**|Numero totale di oggetti creati in questa riga.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che sono stati allocati in questa riga.|  
|**Byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che sono stati allocati in questa riga.|  
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che sono stati allocati in questa riga.|  
  
## Vedere anche  
 [Visualizzazione Righe](../profiling/lines-view-sampling-data.md)