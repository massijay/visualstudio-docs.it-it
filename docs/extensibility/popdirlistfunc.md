---
title: "POPDIRLISTFUNC | Microsoft Docs"
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
  - "POPLISTFUNC"
helpviewer_keywords: 
  - "Funzione di callback POPDIRLISTFUNC"
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si tratta di una funzione di callback specificata per il [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) funzione per aggiornare una raccolta di directory e, facoltativamente, i nomi di file per scoprire che si trovano sotto controllo del codice sorgente.  
  
 Il `POPDIRLISTFUNC` callback deve essere chiamato solo per le directory e i nomi di file \(nell'elenco specificato per il `SccPopulateDirList` funzione\) che sono sotto controllo del codice sorgente.  
  
## Signature  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)( LPVOID pvCallerData, BOOL bFolder, LPCSTR lpDirectoryOrFileName );  
```  
  
## Parametri  
 pvCallerData  
 \[in\] Valore dell'utente assegnato a [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bOpzioni cartella  
 \[in\] `TRUE` Se il nome in `lpDirectoryOrFileName` è una directory; in caso contrario il nome è un nome di file.  
  
 lpDirectoryOrFileName  
 \[in\] Percorso completo a un nome di directory o file incluso nel controllo del codice sorgente.  
  
## Valore restituito  
 Nell'IDE viene restituito un codice di errore appropriato:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Continuare l'elaborazione.|  
|SCC\_I\_OPERATIONCANCELED|Arrestare l'elaborazione.|  
|SCC\_E\_xxx|Qualsiasi errore di controllo di origine appropriato deve arrestare l'elaborazione.|  
  
## Note  
 Se il `fOptions` parametro il `SccPopulateDirList` funzione contiene il `SCC_PDL_INCLUDEFILES` flag, quindi l'elenco conterrà probabilmente i nomi di file, nonché i nomi di directory.  
  
## Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Codici di errore](../extensibility/error-codes.md)