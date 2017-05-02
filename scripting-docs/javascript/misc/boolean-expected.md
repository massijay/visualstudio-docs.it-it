---
title: "Previsto Boolean | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5010"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Previsto Boolean
Si è tentato di richiamare il metodo **Boolean.prototype.toString** o **Boolean.prototype.valueOf** su un tipo di oggetto diverso da `Boolean`.  L'oggetto di questo tipo di chiamata deve essere di tipo `Boolean`.  Di seguito è riportato un esempio:  
  
```javascript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### Per correggere l'errore  
  
-   Richiamare solo i metodi **Boolean.prototype.toString** o **Boolean.prototype.valueOf** su oggetti di tipo **Boolean.**  
  
## Vedere anche  
 [Oggetto Boolean](../../javascript/reference/boolean-object-javascript.md)   
 [Riepilogo dei tipi di dati](../../javascript/data-types-javascript.md)   
 [Controllo del flusso di programma](../../javascript/controlling-program-flow-javascript.md)   
 [Copia, passaggio e confronto di dati](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)