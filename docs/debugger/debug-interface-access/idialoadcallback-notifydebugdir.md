---
title: "IDiaLoadCallback::NotifyDebugDir | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaLoadCallback::NotifyDebugDir (metodo)"
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Chiamato quando una directory debug è stata trovata nel file EXE.  
  
## Sintassi  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### Parametri  
 `fExecutable`  
 \[in\]  `TRUE` se la directory debug viene letta da un eseguibile \(anziché un file di estensione dbg\).  
  
 `cbData`  
 \[in\]  Conteggio di byte dei dati nella directory di debug.  
  
 `data[]`  
 \[in\]  Una matrice che viene soddisfatta di directory debug.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Il codice restituito in genere viene ignorato.  
  
## Note  
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) il metodo richiama questo callback quando viene trovata una directory di debug durante l'elaborazione del file eseguibile.  
  
 Questo metodo cancella la necessità di un client reverse engineering l'eseguibile e\/o il file di debug di supportare le informazioni di debug diverso da quello presente nel file con estensione pdb.  Con questi dati, il client è in grado di riconoscere il tipo di informazioni di debug disponibile e se risiede nel file eseguibile o nel file di estensione dbg.  
  
 La maggior parte dei client non sarà necessario eseguire questa operazione perché callback `IDiaDataSource::loadDataForExe` il metodo trasparente visualizzato sia con estensione pdb che i file di estensione dbg se necessario per fornire i simboli.  
  
## Vedere anche  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)