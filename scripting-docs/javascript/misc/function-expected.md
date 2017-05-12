---
title: "Prevista funzione | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5002"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Prevista funzione
Hai tentato di chiamare uno dei metodi **Function prototype** in un oggetto che non era un oggetto di `Function` o hai utilizzato un oggetto in un contesto di chiamata di funzione.  Ad esempio, il codice seguente genera questo errore perché **example** non è una funzione.  
  
```javascript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### Per correggere l'errore  
  
-   Chiama solo i metodi **Function prototype** sugli oggetti `Function`.  
  
-   Assicurati di utilizzare l'operatore di chiamata di funzione `()` per chiamare solo le funzioni.  
  
## Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Proprietà prototype \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)