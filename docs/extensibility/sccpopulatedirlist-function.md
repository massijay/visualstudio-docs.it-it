---
title: "Funzione SccPopulateDirList | Microsoft Docs"
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
  - "SccPopulateDirList"
helpviewer_keywords: 
  - "Funzione SccPopulateDirList"
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccPopulateDirList
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione determina quali directory e, facoltativamente, i file vengono archiviati nel controllo del codice sorgente fornito un elenco di directory da esaminare.  
  
## Sintassi  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### Parametri  
 pContext  
 \[in\] Il puntatore di contesto plug\-in del controllo di origine.  
  
 nDirs  
 \[in\] Numero di percorsi di directory nel `lpDirPaths` matrice.  
  
 lpDirPaths  
 \[in\] Matrice di percorsi di directory da esaminare.  
  
 pfnPopulate  
 \[in\] Funzione di callback da chiamare per ogni nome del file nel percorso di directory e \(facoltativamente\) `lpDirPaths` \(vedere [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) per informazioni dettagliate\).  
  
 pvCallerData  
 \[in\] Valore che deve essere passato invariato per la funzione di callback.  
  
 Opzioni  
 \[in\] Una combinazione di valori che controllano la modalità di elaborazione delle directory \(vedere la sezione "Flag PopulateDirList" di [Flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) per i valori possibili\).  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Completata l'operazione.|  
|SCC\_E\_UNKNOWNERROR|Si è verificato un errore.|  
  
## Note  
 Solo le directory e, facoltativamente, i nomi di file che sono effettivamente nel repository di controllo di origine vengono passati alla funzione di callback.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Codici di errore](../extensibility/error-codes.md)