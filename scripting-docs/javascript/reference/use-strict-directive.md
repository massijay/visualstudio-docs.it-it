---
title: "Direttiva use strict | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "strict_JavaScriptKeyword"
  - "use strict"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "modalità strict"
  - "direttiva use strict"
  - "use strict"
ms.assetid: b532e8c9-548c-4bbe-b2fc-5459ebd62e56
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Direttiva use strict
Limita l'utilizzo di alcune funzionalità in JavaScript.  Supportato solo in Internet Explorer 10 e nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Sintassi  
  
```javascript  
use strict  
```  
  
## Note  
  
## Esempio  
 Il codice seguente genera un errore di sintassi in quanto in modalità strict tutte le variabili devono essere dichiarate con `var`.  
  
```javascript  
"use strict";  
function testFunction(){  
   var testvar = 4;  
    return testvar;  
}  
intvar = 5;  
  
```  
  
## Vedere anche  
 [Modalità strict](../../javascript/advanced/strict-mode-javascript.md)