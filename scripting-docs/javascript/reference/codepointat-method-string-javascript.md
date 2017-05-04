---
title: "Metodo codePointAt (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo codePointAt (String) (JavaScript)
Restituisce il punto di codice relativo a un carattere UTF\-16 Unicode.  
  
## Sintassi  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### Parametri  
 `stringObj`  
 Obbligatorio.  Oggetto String.  
  
 `pos`  
 Obbligatorio.  Posizione del carattere.  
  
## Note  
 Questo metodo restituisce i valori dei punti di codice, tra cui i punti di codice "astrali" \(punti di codice con più di quattro valori esadecimali\), per tutti i caratteri UTF\-16.  
  
 Se `pos` è minore di zero \(0\) o maggiore delle dimensioni della stringa, il valore restituito è `undefined`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `codePointAt`.  
  
```javascript  
var cp1 = "𠮷".codePointAt(0);  
vary cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]