---
title: "Funzione Debug.msTraceAsyncCallbackCompleted | Microsoft Docs"
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
ms.assetid: 6f9bf139-a6f0-4d91-b7bf-bcc0515de686
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Funzione Debug.msTraceAsyncCallbackCompleted
Indica il completamento dello stack di callback associato a un'operazione asincrona specificata in precedenza.  
  
## Sintassi  
  
```  
Debug.msTraceAsyncCallbackCompleted()  
```  
  
## Note  
 Chiamare questa funzione dopo la chiamata a `Debug.msTraceAsyncCallbackStarting`.  
  
> [!NOTE]
>  Alcuni strumenti di debug non visualizzano le informazioni inviate al debugger.  
  
## Esempio  
 Il codice riportato di seguito fornisce un esempio di traccia di una chiamata asincrona per un'app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
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