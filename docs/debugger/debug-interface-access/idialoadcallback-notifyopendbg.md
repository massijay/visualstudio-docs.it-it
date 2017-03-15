---
title: "IDiaLoadCallback::NotifyOpenDBG | Microsoft Docs"
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
  - "IDiaLoadCallback::NotifyOpenDBG (metodo)"
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::NotifyOpenDBG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Chiamato quando un file candidate dbg è stato aperto.  
  
## Sintassi  
  
```cpp#  
HRESULT NotifyOpenDBG (   
   LPCOLESTR dbgPath,  
   HRESULT   resultCode  
);  
```  
  
#### Parametri  
 `dbgPath`  
 \[in\]  Il percorso completo del file con estensione dbg.  
  
 `resultCode`  
 \[in\]  Il codice che indica l'esito positivo \(`S_OK`\) o errore di caricamento del file.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Il codice restituito in genere viene ignorato.  
  
## Vedere anche  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)