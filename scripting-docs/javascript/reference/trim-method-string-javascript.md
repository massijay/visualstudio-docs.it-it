---
title: "Metodo trim (String) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "trim (metodo)"
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Metodo trim (String) (JavaScript)
Rimuove gli spazi iniziali e finali e i caratteri di terminazione di riga da una stringa.  
  
## Sintassi  
  
```  
  
stringObj.trim()  
```  
  
## Parametri  
 `stringObj`  
 Obbligatorio.  Oggetto `String` o valore letterale stringa.  Questa stringa non viene modificata dal metodo `trim`.  
  
## Valore restituito  
 Stringa originale in cui sono stati rimossi spazi vuoti iniziali e finali e caratteri di terminazione di riga.  
  
## Note  
 I caratteri rimossi includono spazio, tabulazione, avanzamento carta, ritorno a capo e avanzamento riga.  Vedere [Caratteri speciali](../../javascript/advanced/special-characters-javascript.md) per un elenco completo degli spazi vuoti e dei caratteri di terminazione di riga.  
  
 Per un esempio che illustri come implementare il proprio metodo di eliminazione, vedere [Prototipi ed ereditarietà del prototipo](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `trim`.  
  
```javascript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Caratteri speciali](../../javascript/advanced/special-characters-javascript.md)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)   
 [Applicazione di esempio per scorrimento, panoramica e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)