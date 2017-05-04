---
title: "Previsto VBArray | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5013"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Previsto VBArray
È stato fornito un oggetto che non era un safeArray di Visual Basic, quando non era previsto.  
  
```  
new VBArray(safeArray);  
```  
  
 VBArrays è di sola lettura e non può essere creato direttamente.  L'argomento safeArray è un valore VBArray e deve essere ottenuto un valore VBArray prima di essere passato al costruttore `VBArray`.  È possibile solo effettuare questa operazione recuperando il valore da un oggetto ActiveX o da un altro oggetto esistente.  
  
### Per correggere l'errore  
  
-   Assicurati di passare solo gli oggetti **VBArray** al costruttore **VBArray**.  
  
## Vedere anche  
 [Oggetto VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)