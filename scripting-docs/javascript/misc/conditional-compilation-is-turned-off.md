---
title: "Compilazione condizionale disattivata | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Compilazione condizionale disattivata
Si è tentato di utilizzare una variabile di compilazione condizionale senza prima attivare la compilazione condizionale.  L'attivazione della compilazione condizionale indica al compilatore [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] di interpretare gli identificatori che iniziano con @ come variabili di compilazione condizionale.  Questa operazione viene eseguita iniziando il codice condizionale con l'istruzione:  
  
```  
/*@cc_on @*/  
```  
  
### Per correggere l'errore  
  
-   Aggiungere l'istruzione seguente all'inizio del codice condizione:  
  
    ```javascript  
    /*@cc_on @*/  
    ```  
  
## Vedere anche  
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [Istruzione @cc\_on](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [Istruzione @if](../../javascript/reference/at-if-statement-javascript.md)   
 [Istruzione @set](../../javascript/reference/at-set-statement-javascript.md)