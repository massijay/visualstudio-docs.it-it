---
title: "Funzione Promise.reject (Promise) | Microsoft Docs"
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Funzione Promise.reject (Promise)
Crea una nuova promessa rifiutata con un risultato uguale all'argomento passato.  
  
## Sintassi  
  
```  
Promise.reject(r);  
```  
  
#### Parametri  
 `r`  
 Obbligatorio.  Il motivo per cui è stata rifiutata la promessa.  
  
## Note  
 La funzione di gestione degli errori del metodo `then` o `catch` viene eseguita quando viene restituita la promessa rifiutata.  
  
## Esempio  
  
```javascript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vedere anche  
 [Oggetto Promise](../../javascript/reference/promise-object-javascript.md)