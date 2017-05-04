---
title: "Il numero delle cifre frazionarie non &#232; compreso nell&#39;intervallo | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5026"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dbe05d7d-fcf6-4823-9c61-4b814d1ad3c4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Il numero delle cifre frazionarie non &#232; compreso nell&#39;intervallo
Si è tentato di passare un argomento non valido alla funzione **Number.prototype.toExponential**.  L'argomento della funzione **toExponential\(\)** deve essere compreso tra 0 e 20 \(inclusi\).  
  
### Per correggere l'errore  
  
-   Verificare che l'argomento in **toExponential\(\)** non sia troppo grande o troppo piccolo.  
  
## Vedere anche  
 [Metodo toExponential \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)