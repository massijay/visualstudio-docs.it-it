---
title: "Previsto oggetto Enumerator | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5015"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Previsto oggetto Enumerator
Si è tentato di richiamare il metodo **Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** o **Enumerator.prototype.moveNext**  in un oggetto di un tipo diverso da `Enumerator`.  L'oggetto di questo tipo di chiamata deve essere di tipo `Enumerator`.  Ecco un esempio di codice che infrange questa regola:  
  
```javascript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### Per correggere l'errore  
  
-   Richiamare solo i metodi **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, o **Enumerator.prototype.moveNext** negli oggetti del tipo `Enumerator`.  Per verificare se l'oggetto è un oggetto di `Enumerator`, utilizzare:  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## Vedere anche  
 [Oggetto Enumerator](../../javascript/reference/enumerator-object-javascript.md)