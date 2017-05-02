---
title: "Prevista stringa | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5005"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4c214c4b-9cd7-473b-8d90-2344c0375c25
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Prevista stringa
Si è tentato di richiamare il metodo **String.prototype.toString** o **String.prototype.valueOf** su un tipo di oggetto diverso da `String`.  L'oggetto di questo tipo di chiamata deve essere di tipo `String`.  
  
### Per correggere l'errore  
  
-   Richiamare solo i metodi **String.prototype.toString** o **String.prototype.valueOf** su oggetti di tipo `String`.  
  
## Vedere anche  
 [Oggetto String](../../javascript/reference/string-object-javascript.md)   
 [Metodo toString \(Object\)](../../javascript/reference/tostring-method-object-javascript.md)