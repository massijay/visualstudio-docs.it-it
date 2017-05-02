---
title: "Funzione Promise.resolve (Promise) | Microsoft Docs"
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Funzione Promise.resolve (Promise)
Crea una nuova promessa risolta con un risultato uguale al relativo argomento.  
  
## Sintassi  
  
```  
Promise.resolve(x)  
```  
  
#### Parametri  
 `x`  
 Obbligatorio.  Valore restituito della promessa completata.  
  
## Note  
 La funzione di gestione dell'evasione del metodo `then` viene eseguita alla restituzione dell'oggetto promise completato.  
  
## Esempio  
  
```javascript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vedere anche  
 [Oggetto Promise](../../javascript/reference/promise-object-javascript.md)