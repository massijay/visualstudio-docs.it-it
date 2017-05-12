---
title: "Metodo toString (Error) | Microsoft Docs"
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
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Metodo toString (Error)
Restituisce una rappresentazione in forma di stringa di un errore.  
  
## Sintassi  
  
```  
  
error.toString()  
```  
  
## Parametri  
 `date`  
 Obbligatorio.  Errore da rappresentare come stringa.  
  
## Valore restituito  
 Restituisce "Errore:" seguito dal messaggio di errore.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `toString` con un errore.  
  
```javascript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]