---
title: "Assegnazione a un risultato di funzione non consentita | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5003"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Assegnazione a un risultato di funzione non consentita
Tenta di assegnare un valore al risultato di una funzione.  Il risultato di una funzione può essere assegnato a una variabile, ma non può essere utilizzato come variabile.  Se desideri assegnare un nuovo valore alla funzione stessa, omettere le parentesi, ovvero l'operatore di chiamata della funzione.  Nell'esempio seguente viene illustrata una situazione in cui verrà generato l'errore.  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### Per correggere l'errore  
  
-   Non utilizzare il valore restituito da una chiamata di funzione come elemento a cui *assegnare un valore*.  Puoi invece assegnare il risultato di una chiamata di funzione *a una variabile*.  
  
    ```javascript  
    myVar = myFunction(42);  
    ```  
  
-   In alternativa, puoi assegnare a una variabile la funzione stessa e non il valore da essa restituito.  
  
    ```javascript  
    myFunction = new Function("return 42;");  
    ```  
  
## Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Scrittura di codice JavaScript](../../javascript/writing-javascript-code.md)   
 [Funzioni](../../javascript/functions-javascript.md)