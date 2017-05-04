---
title: "Funzione Debug.msUpdateAsyncCallbackRelation | Microsoft Docs"
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
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Funzione Debug.msUpdateAsyncCallbackRelation
Aggiorna lo stato della relazione tra un elemento di lavoro sincrono e l'operazione asincrona associata.  
  
## Sintassi  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### Parametri  
 `relatedAsyncOperationId`  
 Obbligatorio.  ID associato all'operazione asincrona.  
  
 `relationType`  
 Facoltativo.  Valore che specifica lo stato della relazione.  
  
## Note  
 L'elemento di lavoro sincrono è in genere la funzione di callback dell'operazione asincrona.  Questa funzione può essere chiamata quando viene interrotta un'operazione asincrona, quando viene utilizzata un'operazione di join o in altri scenari.  
  
 I valori possibili per `relationType` includono:  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 Per ulteriori informazioni, vedere [Costanti debug](../../javascript/reference/debug-constants.md).  
  
> [!NOTE]
>  Alcuni strumenti di debug non visualizzano le informazioni inviate al debugger da questa funzione.  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]