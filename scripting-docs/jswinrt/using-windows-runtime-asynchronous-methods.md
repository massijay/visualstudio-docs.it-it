---
title: "Utilizzo di metodi asincroni di Windows Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Metodi asincroni di Windows Runtime"
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Utilizzo di metodi asincroni di Windows Runtime
Molti metodi di Windows Runtime, in particolari i metodi il cui completamento richiede molto tempo, sono asincroni.  Questi metodi restituiscono in genere un'azione o un'operazione asincrona, ad esempio, `Windows.Foundation.IAsyncAction`, `Windows.Foundation.IAsyncOperation`, `Windows.Foundation.IAsyncActionWithProgress` o `Windows.Foundation.IAsyncOperationWithProgress`.  Questi metodi sono rappresentati in JavaScript dal modello [CommonJS\/Promises\/A](http://go.microsoft.com/fwlink/p/?LinkId=244434).  Restituiscono quindi un oggetto Promise che include una funzione [then](http://msdn.microsoft.com/it-it/c63904fc-465b-4fd5-a1d6-e4fb200248e7), per cui è necessario fornire una funzione `completed` che gestisce il risultato in caso di esito positivo dell'operazione.  Se non si vuole fornire alcun gestore degli errori, è consigliabile usare la funzione [done](http://msdn.microsoft.com/it-it/9a5e6877-a2cf-421f-a91e-37d84ccb40da) invece della funzione [then](http://msdn.microsoft.com/it-it/c63904fc-465b-4fd5-a1d6-e4fb200248e7).  
  
> [!IMPORTANT]
>  Le funzionalità di Windows Runtime non sono disponibili per app eseguite in Internet Explorer.  
  
## Esempi di metodi asincroni  
 Nell'esempio seguente la funzione [then](http://msdn.microsoft.com/it-it/c63904fc-465b-4fd5-a1d6-e4fb200248e7) accetta un parametro che rappresenta il valore completo del metodo `createResourceAsync`.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 In questo caso, se il metodo `createResourceAsync` ha esito negativo, restituisce una promessa nello stato di errore, ma non genera eccezioni.  È possibile gestire un errore usando la funzione [then](http://msdn.microsoft.com/it-it/c63904fc-465b-4fd5-a1d6-e4fb200248e7) come indicato di seguito.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 Se non si vuole gestire l'errore in modo esplicito, ma si vuole che generi un'eccezione, è possibile usare invece la funzione [done](http://msdn.microsoft.com/it-it/9a5e6877-a2cf-421f-a91e-37d84ccb40da).  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 È anche possibile visualizzare lo stato relativo al completamento usando una terza funzione.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            },  
    // Error.  
            function(error) {   
               alert("Failed to create a resource.");  
            },  
    // Progress.  
            function(progress, resultSoFar) {   
               setProgressBar(progress);  
            });  
```  
  
 Per altre informazioni sulla programmazione asincrona, vedere [Asynchronous programming](http://msdn.microsoft.com/it-it/904ff97c-bb36-4ac5-9eda-a961e3639415).  
  
## Vedere anche  
 [Utilizzo di Windows Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)