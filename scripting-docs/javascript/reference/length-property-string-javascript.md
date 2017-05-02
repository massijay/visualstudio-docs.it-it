---
title: "Propriet&#224; length (String) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "stringhe [Visual Studio], length"
  - "Length (proprietà)"
  - "length (proprietà) (String)"
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Propriet&#224; length (String) (JavaScript)
Restituisce la lunghezza di un oggetto `String`.  
  
> [!WARNING]
>  Le stringhe JavaScript sono immutabili, per cui la loro lunghezza non può essere modificata.  
  
## Sintassi  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## Note  
 La proprietà `length` contiene un Integer che indica il numero di caratteri inclusi nell'oggetto `String`.  L'ultimo carattere nell'oggetto `String` ha un indice di `length` uguale a \- 1.  
  
## Esempio  
 Nel codice seguente viene illustrato come utilizzare `length`.  Le stringhe JavaScript sono immutabile e non possono essere modificate sul posto.  Tuttavia, puoi scrivere la stringa invertita in una matrice e chiamare `join` con il carattere vuoto, che produce una stringa senza caratteri separatori.  
  
```javascript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]