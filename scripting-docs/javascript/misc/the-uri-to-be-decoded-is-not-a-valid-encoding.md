---
title: "La codifica utilizzata per l&#39;URI da decodificare non &#232; corretta | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5025"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# La codifica utilizzata per l&#39;URI da decodificare non &#232; corretta
Si è tentato di decodificare un URI \(Uniform Resource Identifier\) non corretto.  Gli URI hanno una sintassi speciale. La maggior parte dei caratteri non alfanumerici deve essere codificata prima di poter essere utilizzata in un URI.  Per creare un URI da una normale stringa [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], è possibile utilizzare i metodi `encodeURI` e `encodeURIComponent`.  
  
 Un URI completo è composto da una sequenza di componenti e separatori.  La forma generale è la seguente:  
  
```javascript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 I nomi racchiusi tra parentesi angolari rappresentano i componenti e i segni ":", "\/", ";" e "?" sono caratteri riservati utilizzati come separatori.  
  
### Per correggere l'errore  
  
-   Assicurarsi che nel codice si tenti di decodificare solo URI validi.  Non è possibile decodificare normali stringhe [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], in quanto possono contenere caratteri non validi.  
  
## Vedere anche  
 [Funzione decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Funzione decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)