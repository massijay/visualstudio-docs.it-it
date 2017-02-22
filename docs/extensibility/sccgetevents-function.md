---
title: "Funzione SccGetEvents | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetEvents"
helpviewer_keywords: 
  - "Funzione SccGetEvents"
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccGetEvents
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione recupera un evento di stato in coda.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### Parametri  
 pvContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 lpFileName  
 \[in, out\] Buffer in cui il plug\-in del controllo del codice sorgente inserisce il nome del file restituito \(fino a caratteri MAX\_PATH\).  
  
 lpStatus  
 \[in, out\] Restituisce il codice di stato \(vedere [Codice di stato file](../extensibility/file-status-code-enumerator.md) per i valori possibili\).  
  
 pnEventsRemaining  
 \[in, out\] Restituisce i numero di voci lasciato nella coda dopo questa chiamata. Se questo numero è elevato, il chiamante può decidere di chiamare il [SccQueryInfo](../extensibility/sccqueryinfo-function.md) per ottenere tutte le informazioni in una sola volta.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Ottenere gli eventi ha avuto esito positivo.|  
|SCC\_E\_OPNOTSUPPORTED|Questa funzione non è supportata.|  
|SCC\_E\_NONSPECIFICERROR|Errore non specificato.|  
  
## Note  
 Questa funzione viene chiamata durante l'elaborazione inattive per vedere se si sono verificati eventuali aggiornamenti di stato per i file di controllo del codice sorgente. Il plug\-in del controllo del codice sorgente gestisce lo stato di tutti i file che conosce e ogni volta che una modifica dello stato è indicato il plug\-in, lo stato e i file associato vengono archiviati in una coda. Quando `SccGetEvents` viene chiamato, nella parte superiore dell'elemento della coda viene recuperato e restituito. Questa funzione è vincolata da restituire solo le informazioni memorizzate nella cache e deve avere molto rapidi \(vale a dire, non la lettura del disco o che richiede il controllo del codice sorgente per lo stato\); in caso contrario, le prestazioni dell'IDE potrebbero iniziare a diminuire.  
  
 Se è presente alcun aggiornamento di stato al report, il plug\-in del controllo del codice sorgente archivia una stringa vuota nel buffer a cui puntato `lpFileName`. In caso contrario, il plug\-in archivia il nome e percorso completo del file per cui è stato modificato le informazioni sullo stato e restituisce il codice di stato appropriato \(uno dei valori descritti in dettaglio in [Codice di stato file](../extensibility/file-status-code-enumerator.md)\).  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Codice di stato file](../extensibility/file-status-code-enumerator.md)