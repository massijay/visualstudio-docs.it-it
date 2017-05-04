---
title: "La funzione non ha un oggetto prototipo valido | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# La funzione non ha un oggetto prototipo valido
Si è tentato di utilizzare **instanceof** per determinare se un oggetto è stato derivato da una particolare classe di funzione, ma è stata ridefinita la proprietà `prototype` dell'oggetto come `null` o come un tipo di oggetto esterno \(nessuno dei quali è un oggetto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valido\).  Un oggetto esterno può essere un oggetto del modello a oggetti host, ad esempio un oggetto finestra o documento di Internet Explorer, o un oggetto COM esterno.  
  
### Per correggere l'errore  
  
-   Assicurarsi che la proprietà `prototype` della funzione faccia riferimento a un oggetto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valido.  
  
## Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Proprietà prototype \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)