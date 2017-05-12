---
title: "La precisione non &#232; compresa nell&#39;intervallo | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5027"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c16760ac-fc08-49d7-8878-9bc434b3c080
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# La precisione non &#232; compresa nell&#39;intervallo
Si è tentato di passare un argomento non valido alla funzione **Number.prototype.toPrecision**.  L'argomento di **toPrecision** deve essere compreso tra 1 e 21 \(inclusi\).  
  
### Per correggere l'errore  
  
-   Verificare che l'argomento di `toPrecision` non sia troppo grande o troppo piccolo.  
  
## Vedere anche  
 [Metodo toPrecision \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)