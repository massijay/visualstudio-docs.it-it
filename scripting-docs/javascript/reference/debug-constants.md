---
title: "Costanti DEBUG | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Costanti DEBUG
Le costanti debug restituiscono valori costanti che sono proprietà dell'oggetto `Debug`.  
  
## Costanti debug dell'oggetto  
 Nella tabella seguente sono elencati i valori costanti che sono proprietà dell'[oggetto Debug](../../javascript/reference/debug-object-javascript.md).  
  
|Costante|Descrizione|Valore|  
|--------------|-----------------|------------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|L'elemento di lavoro sincrono ha assegnato un callback o una continuazione da eseguire tramite un'operazione asincrona.|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|L'elemento di lavoro sincrono ha soddisfatto parte di un'operazione asincrona di join.|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|L'elemento di lavoro sincrono ha soddisfatto un'operazione asincrona di scelta.|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|L'elemento di lavoro sincrono è stato annullato.|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|L'elemento di lavoro sincrono ha generato un errore in un'operazione asincrona.|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|Operazione asincrona completata.|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|Operazione asincrona annullata.|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|L'operazione asincrona ha restituito un errore.|3|  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [Funzione Debug.msTraceAsyncOperationCompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Funzione Debug.msUpdateAsyncCallbackRelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)