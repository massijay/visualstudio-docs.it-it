---
title: "Commento senza terminazione | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Commento senza terminazione
Avviato un blocco di commenti a più righe, ma non è terminato correttamente.  I commenti a più righe iniziano con una combinazione "\/\*" e terminano con la combinazione opposta "\*\/".  Di seguito è riportato un esempio:  
  
```javascript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### Per correggere l'errore  
  
-   Assicurarsi di terminare i commenti a più righe con la combinazione "\*\/".  
  
## Vedere anche  
 [Istruzioni per commenti](../../javascript/reference/comment-statements-javascript.md)