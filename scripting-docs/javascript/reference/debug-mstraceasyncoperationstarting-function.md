---
title: "Funzione Debug.msTraceAsyncOperationStarting | Microsoft Docs"
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
ms.assetid: c8458264-07e0-4cd6-8528-ff7cf009cf9e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Funzione Debug.msTraceAsyncOperationStarting
Inizializza una traccia per un'operazione asincrona.  
  
## Sintassi  
  
```  
Debug.msTraceAsyncOperationStarting(operationName)  
```  
  
#### Parametri  
 `operationName`  
 Obbligatorio.  Una stringa che identifica l'operazione asincrona.  Se `operationName` ha valore Null o non definito, per il nome dell'operazione viene utilizzata una stringa vuota.  
  
## Valore restituito  
 Integer che rappresenta l'ID dell'operazione.  
  
## Note  
 Chiamare questo metodo prima dell'avvio dell'operazione asincrona.  
  
> [!NOTE]
>  Alcuni strumenti di debug non visualizzano le informazioni inviate al debugger.  
  
## Esempio  
 Il codice riportato di seguito fornisce un esempio di instrumentazione di una chiamata asincrona per un'app [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
```javascript  
function asyncWrapperFunction() {  
    var opID = Debug.msTraceAsyncOperationStarting('async trace');  
    doSomethingAsync().then(function (result) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_SUCCESS);  
        Debug.msTraceAsyncCallbackStarting(opID);  
        // Process result of async operation.  
    }, function (error) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_ERROR);  
        Debug.msTraceAsyncCallbackStarting(opID);  
    });  
  
    Debug.msTraceAsyncCallbackCompleted();  
}  
  
function doSomethingAsync() {  
    return WinJS.Promise.as(true);  
}  
  
asyncWrapperFunction();  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]