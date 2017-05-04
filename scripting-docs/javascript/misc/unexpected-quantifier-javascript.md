---
title: "Quantificatore imprevisto (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Quantificatore imprevisto (JavaScript)
Durante la composizione del modello di ricerca di espressioni regolari, è stato creato un elemento del modello con un fattore di ripetizione non valido.  Ad esempio, il modello  
  
```  
/^+/  
```  
  
 non è valido perché l'elemento ^, ovvero l'inizio dell'input, non può avere un fattore di ripetizione.  Nella tabella seguente sono elencati gli elementi che non possono avere fattori di ripetizione.  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|^|Inizio dell'input|  
|$|Fine dell'input|  
|\\b|Confine di parola|  
|\\B|Carattere che non costituisce un confine di parola|  
|\*|Zero o più ripetizioni|  
|\+|Una o più ripetizioni|  
|?|Zero o una ripetizione|  
|{n}|n ripetizioni|  
|{n,}|n o più ripetizioni|  
|{n,m}|Ripetizioni da n a m, incluse|  
  
### Per correggere l'errore  
  
-   Assicurarsi che l'elemento del modello di ricerca contenga solo i fattori di ripetizione validi.  
  
## Vedere anche  
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)