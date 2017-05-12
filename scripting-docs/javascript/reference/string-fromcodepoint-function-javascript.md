---
title: "Funzione String.fromCodePoint (JavaScript) | Microsoft Docs"
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
ms.assetid: 7c4c057b-c67a-4b10-afdd-4f75c7c5988c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione String.fromCodePoint (JavaScript)
Restituisce la stringa associata a un punto di codice UTF\-16 Unicode.  
  
## Sintassi  
  
```  
String.fromCodePoint(...codePoints);  
```  
  
#### Parametri  
 `…codePoints`  
 Obbligatorio.  Parametro rest che specifica uno o più valori di punti di codice UTF\-16.  
  
## Note  
 Questa funzione genera un'eccezione `RangeError` se `...codePoints` non è un punto di codice UTF\-16 valido.  
  
## Esempio  
 L'esempio seguente illustra come usare la funzione `fromCodePoint`.  
  
```javascript  
var str1 = String.fromCodePoint(0x20BB7);  
var str2 = String.fromCodePoint(98);  
var str3 = String.fromCodePoint(97, 98, 99);  
  
if(console && console.log) {  
    console.log(str1);  
    console.log(str2);  
    console.log(str3);  
}  
  
// Output:  
// 𠮷  
// b  
// abc  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]