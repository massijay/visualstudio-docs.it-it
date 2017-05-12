---
title: "Propriet&#224; Debug.setNonUserCodeExceptions | Microsoft Docs"
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
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Propriet&#224; Debug.setNonUserCodeExceptions
Determina se un blocco try\-catch in questo ambito deve essere considerato dal debugger come non gestito dall'utente.  Le eccezioni possono essere classificate come generate, non gestite dall'utente o non gestite.  
  
 Se questa proprietà è impostata a `true` in un determinato ambito, il debugger può quindi decidere di intraprendere qualche azione \(ad esempio, interruzione\) sulle eccezioni generate in quell'ambito se lo sviluppatore desidera interrompere le eccezioni non gestite dall'utente.  Se questa proprietà è impostata a `false` equivale ad una proprietà che non è stata mai impostata.  
  
 Per ulteriori informazioni sul debug, vedere l'[overview di debug Active Script](http://go.microsoft.com/fwlink/p/?LinkId=249469).  
  
## Sintassi  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## Esempio  
 Nel seguente codice viene mostrato come impostare questa proprietà.  
  
```javascript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]