---
title: "L&#39;URI da codificare contiene un carattere non valido | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5024"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# L&#39;URI da codificare contiene un carattere non valido
Si è tentato di codificare come URI \(Uniform Resource Identifier\) una stringa contenente caratteri non validi.  Sebbene la maggior parte dei caratteri sia valida all'interno delle stringhe da convertire in URI, alcune sequenze di caratteri Unicode non sono valide.  
  
### Per correggere l'errore  
  
-   Assicurarsi che la stringa da codificare contenga solo sequenze Unicode valide.  Un URI completo è composto da una sequenza di componenti e separatori.  I nomi racchiusi tra parentesi angolari rappresentano i componenti e i segni ":", "\/", ";" e "?" sono caratteri riservati utilizzati come separatori.  La forma generale è la seguente:  
  
    ```javascript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## Vedere anche  
 [Funzione encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Funzione encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)