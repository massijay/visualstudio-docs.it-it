---
title: "Previsto un oggetto di espressione regolare | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Previsto un oggetto di espressione regolare
Si è tentato di richiamare il metodo **RegExp.prototype.toString** o **RegExp.prototype.valueOf** su un tipo di oggetto diverso da `RegExp`.  L'oggetto di questo tipo di chiamata deve essere di tipo `RegExp`.  
  
### Per correggere l'errore  
  
-   Richiamare solo i metodi **RegExp.prototype.toString** o **RegExp.prototype.valueOf** su oggetti di tipo `RegExp`.  
  
## Vedere anche  
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)