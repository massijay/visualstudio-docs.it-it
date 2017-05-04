---
title: "Identificatore non definito | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5009"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 8c8000d9-dd14-487e-922d-98430024a0f6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Identificatore non definito
Si è tentato di utilizzare un identificatore che il compilatore [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] non riconosce.  Il valore non definito viene restituito ogni volta che si utilizza:  
  
-   una variabile che non esiste;  
  
-   una variabile dichiarata, ma a cui non è mai stato assegnato un valore;  
  
-   la proprietà di un oggetto che non esiste.  
  
### Per correggere l'errore  
  
-   Dichiarare la variabile con un'istruzione **var** \(ad esempio in `var` x;\).  
  
## Vedere anche  
 [Variabili](../../javascript/variables-javascript.md)   
 [Ambito della variabile](../../javascript/advanced/variable-scope-javascript.md)