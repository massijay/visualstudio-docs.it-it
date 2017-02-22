---
title: "IDiaFrameData::execute | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaFrameData::execute (metodo)"
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esegue la rimozione dello stack e restituisce i risultati in un'interfaccia del frame dello stack.  
  
## Sintassi  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### Parametri  
 `frame`  
 \[in\]   [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) oggetto che utilizza lo stato dei registri del frame.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Nella tabella seguente vengono illustrati i valori restituiti possibili di questo metodo.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|E\_DIA\_INPROLOG|Non è possibile eseguire uno stack frame mentre nel codice di prologo.|  
|E\_DIA\_SYNTAX|Errore di analisi individuato nel programma frame.|  
|E\_DIA\_FRAME\_ACCESS|Impossibile accedere ai registri o memoria.|  
|E\_DIA\_VALUE|Errore nel calcolo di un valore \(ad esempio, divisione per zero\).|  
  
## Note  
 Questo metodo viene chiamato durante il debug per rimuovere lo stack.  [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) l'oggetto viene implementato dall'applicazione client ottenere gli aggiornamenti nei log e fornire i metodi utilizzati da  `execute` metodo.  
  
## Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)