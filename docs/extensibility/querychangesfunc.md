---
title: "QUERYCHANGESFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "QUERYCHANGESFUNC"
helpviewer_keywords: 
  - "Funzione di callback QUERYCHANGESFUNC"
  - "Struttura QUERYCHANGESDATA"
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si tratta di una funzione di callback utilizzata dal [SccQueryChanges](../extensibility/sccquerychanges-function.md) operazione per enumerare una raccolta di nomi di file e determinare lo stato di ogni file.  
  
 Il `SccQueryChanges` ha un elenco di file e un puntatore a funzione di `QUERYCHANGESFUNC` callback. Il plug\-in del controllo del codice sorgente enumera l'elenco specificato e fornisce lo stato \(tramite questo callback\) per ogni file nell'elenco.  
  
## Signature  
  
```cpp#  
typedef BOOL (*QUERYCHANGESFUNC)( LPVOID pvCallerData, QUERYCHANGESDATA * pChangesData );  
```  
  
## Parametri  
 pvCallerData  
 \[in\] Il `pvCallerData` parametro passato dal chiamante \(IDE\) di [SccQueryChanges](../extensibility/sccquerychanges-function.md). Il plug\-in del controllo del codice sorgente necessario non fare supposizioni sul contenuto di questo valore.  
  
 pChangesData  
 \[in\] Puntatore a un [Struttura QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) struttura che descrive le modifiche in un file.  
  
## Valore restituito  
 Nell'IDE viene restituito un codice di errore appropriato:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Continuare l'elaborazione.|  
|SCC\_I\_OPERATIONCANCELED|Arrestare l'elaborazione.|  
|SCC\_E\_xxx|Qualsiasi errore SCC appropriato deve arrestare l'elaborazione.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> Struttura QUERYCHANGESDATA  
 La struttura passata per ogni file è simile al seguente:  
  
```cpp#  
struct QUERYCHANGESDATA_A { DWORD  dwSize; LPCSTR lpFileName; DWORD  dwChangeType; LPCSTR lpLatestName; }; typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA; struct QUERYCHANGESDATA_W { DWORD   dwSize; LPCWSTR lpFileName; DWORD   dwChangeType; LPCWSTR lpLatestName; };  
```  
  
 dwSize  
 Dimensione della struttura \(in byte\).  
  
 lpFileName  
 Nome del file originale per questo elemento.  
  
 dwChangeType  
 Codice che indica lo stato del file:  
  
|Codice|Descrizione|  
|------------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|Impossibile stabilire cosa è cambiato.|  
|`SCC_CHANGE_UNCHANGED`|Nessuna modifica nome per il file.|  
|`SCC_CHANGE_DIFFERENT`|File con un'identità diversa, ma lo stesso nome esiste nel database.|  
|`SCC_CHANGE_NONEXISTENT`|File non esiste nel database o in locale.|  
|`SCC_CHANGE_DATABASE_DELETED`|File eliminato dal database.|  
|`SCC_CHANGE_LOCAL_DELETED`|File eliminati localmente, ma il file esiste ancora nel database. Se questo non può essere determinato, restituire `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|File aggiunti al database ma non esiste in locale.|  
|`SCC_CHANGE_LOCAL_ADDED`|File non esiste nel database e un nuovo file locale.|  
|`SCC_CHANGE_RENAMED_TO`|File rinominati o spostati nel database come `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|File rinominati o spostati nel database da `lpLatestName`; Se questo è troppo costoso da rilevare, restituiscono un contrassegno diverso, ad esempio `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 Il nome di file corrente per questo elemento.  
  
## Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Codici di errore](../extensibility/error-codes.md)