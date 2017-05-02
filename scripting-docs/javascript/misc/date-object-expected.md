---
title: "Previsto oggetto Date | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5006"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Previsto oggetto Date
Si è tentato di richiamare il metodo **Date.prototype.toString** o **Date.prototype.valueOf** su un oggetto di un tipo diverso da `Date`.  L'oggetto di questo tipo di chiamata deve essere di tipo `Date`.  Di seguito è riportato un esempio:  
  
```javascript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### Per correggere l'errore  
  
-   Richiamare solo i metodi **Date.prototype.toString** o **Date.prototype.valueOf** sugli oggetti del tipo `Date`.  
  
## Vedere anche  
 [Oggetto Date](../../javascript/reference/date-object-javascript.md)   
 [Metodo getDate \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Oggetti intrinseci](../../javascript/intrinsic-objects-javascript.md)