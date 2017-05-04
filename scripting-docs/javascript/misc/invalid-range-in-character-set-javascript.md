---
title: "Intervallo non valido nel set di caratteri (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5021"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Intervallo non valido nel set di caratteri (JavaScript)
Hai tentato di creare un'espressione regolare con un intervallo del set di caratteri non valido.  I set di caratteri devono essere compresi solo tra caratteri singoli, ad esempio tra a e z oppure tra 0 e 9, e le classi di caratteri come \\w non possono essere incluse in un set di caratteri.  Il primo carattere dell'intervallo deve inoltre precedere il secondo carattere incluso nell'intervallo.  Di seguito è riportato un esempio:  
  
```javascript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### Per correggere l'errore  
  
-   Utilizza solo i caratteri singoli per comporre il set di caratteri dell'espressione regolare e assicurati che siano nell'ordine corretto.  
  
## Vedere anche  
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)