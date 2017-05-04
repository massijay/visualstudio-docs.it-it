---
title: "Metodo repeat (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo repeat (String) (JavaScript)
Restituisce un nuovo oggetto stringa con un valore uguale alla stringa originale ripetuto per il numero specificato di volte.  
  
## Sintassi  
  
```  
stringObj.repeat(count);  
```  
  
#### Parametri  
 `stringObj`  
 Obbligatorio.  Oggetto stringa.  
  
 `count`  
 Obbligatorio.  Numero di volte per cui ripetere la stringa originale nella stringa restituita.  
  
## Eccezioni  
 Questo metodo genera un oggetto RangeError se e solo se l'argomento è negativo o \+Infinity.  
  
## Note  
 Il metodo `repeat` concatena la stringa originale alla nuova stringa per il numero di volte specificato da `count`.  
  
 Questo metodo genera un errore se `count` non è un numero positivo minore di `Infinity`.  
  
## Esempio  
  
```javascript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]