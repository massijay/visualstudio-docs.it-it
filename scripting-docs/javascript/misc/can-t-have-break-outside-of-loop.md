---
title: "Impossibile utilizzare &#39;break&#39; all&#39;esterno di un ciclo | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Impossibile utilizzare &#39;break&#39; all&#39;esterno di un ciclo
Si è tentato di utilizzare la parola chiave **break** all'esterno di un ciclo.  La parola chiave **break** viene utilizzata per terminare un ciclo o un'istruzione `switch`.  Deve essere incorporata nel corpo di un ciclo o di un'istruzione `switch`.  Tuttavia, **label** può seguire la parola chiave break.  
  
```  
break labelname;  
```  
  
 È necessario disporre solo del form etichettato della parola chiave **break** quando si utilizzano istruzioni `switch` o cicli annidati ed è necessario uscire da un ciclo che non è quello più interno.  
  
### Per correggere l'errore  
  
-   Assicurarsi che la parola chiave **break** sia visualizzata all'interno di un ciclo o di un'istruzione switch di inclusione.  
  
## Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Controllo del flusso di programma](../../javascript/controlling-program-flow-javascript.md)   
 [Risoluzione dei problemi negli script](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)