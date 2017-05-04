---
title: "Funzione String.fromCharCode (JavaScript) | Microsoft Docs"
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
  - "fromCharCode"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fromCharCodeAt (metodo)"
  - "caratteri, da Unicode"
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione String.fromCharCode (JavaScript)
Restituisce una stringa a partire da un numero di valori dei caratteri Unicode.  
  
## Sintassi  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## Parametri  
 `String`  
 Obbligatorio.  Oggetto `String`.  
  
 `code1`, . . . , `codeN`  
 Facoltativo.  Serie di valori del carattere Unicode da convertire in una stringa.  Se non viene specificato alcun argomento, il risultato sarà una stringa vuota.  
  
## Note  
 Chiama questa funzione nell'oggetto `String` anziché in un'istanza di stringa.  
  
 Nell'esempio seguente viene illustrato come utilizzare questo metodo:  
  
```javascript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vedere anche  
 [Metodo charCodeAt \(String\)](../../javascript/reference/charcodeat-method-string-javascript.md)