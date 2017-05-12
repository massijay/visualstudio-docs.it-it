---
title: "Riferimento circolare nell&#39;argomento value non supportato | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5034"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Riferimento circolare nell&#39;argomento value non supportato
È stato effettuato un tentativo di richiamare `JSON.stringify` con un valore non valido.  L'argomento `value`, una matrice o un oggetto, contiene un riferimento circolare.  
  
### Per correggere l'errore  
  
-   Rimuove il riferimento circolare dall'argomento.  
  
## Esempio  
 Il codice in questo esempio genera un errore di runtime perché `john` include un riferimento a `mary` e `mary` include un riferimento a `john`.  Per rimuovere il riferimento circolare, rimuovere o annullare l'impostazione della proprietà `brother` dall'oggetto `mary` o la proprietà `sister` dall'oggetto `john`.  
  
```javascript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## Vedere anche  
 [Oggetto JSON](../../javascript/reference/json-object-javascript.md)   
 [Funzione JSON.parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Errori di runtime JavaScript](../../javascript/reference/javascript-run-time-errors.md)