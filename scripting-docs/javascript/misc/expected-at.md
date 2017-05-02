---
title: "Previsto &#39;@&#39; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1032"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Previsto &#39;@&#39;
Si è tentato di creare una variabile da utilizzare con istruzioni di compilazione condizionale utilizzando l'istruzione `@set`, ma non è stato posizionato il simbolo "**@**" prima del nome della variabile.  
  
### Per correggere l'errore  
  
-   Aggiungere il simbolo "**@**" immediatamente prima del nome della variabile.  Di seguito è riportato un esempio:  
  
    ```javascript  
    @set @myvar = 1  
    ```  
  
## Vedere anche  
 [Istruzione @set](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)