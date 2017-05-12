---
title: "La parola chiave &#39;throw&#39; deve essere seguita da un&#39;espressione nella stessa riga di codice sorgente | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1035"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# La parola chiave &#39;throw&#39; deve essere seguita da un&#39;espressione nella stessa riga di codice sorgente
È stata utilizzata la parola chiave `throw` non seguita da un'espressione sulla stessa riga di codice sorgente.  Un'istruzione `throw` è costituita da due parti, ovvero la parola chiave `throw` seguita dall'espressione da generare.  Di seguito è riportato un esempio:  
  
```javascript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Non è possibile suddividere questi due componenti.  
  
### Per correggere l'errore  
  
-   Assicurarsi che la parola chiave `throw` e l'espressione da generare vengano visualizzate sulla stessa riga.  
  
## Vedere anche  
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)   
 [Istruzione throw](../../javascript/reference/throw-statement-javascript.md)   
 [Istruzione try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)