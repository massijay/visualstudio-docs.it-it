---
title: "Metodo subarray (Float64Array) | Microsoft Docs"
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
ms.assetid: f3c24e1b-5fb2-49a1-8183-0fda33dbeaba
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Metodo subarray (Float64Array)
Ottiene una nuova visualizzazione Float64Array dell'archivio [Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) per questa matrice, specificando il primo e l'ultimo membro della sottomatrice.  
  
## Sintassi  
  
```javascript  
var newFloat64Array = float64Array.subarray(begin, end);  
```  
  
## Parametri  
 `newFloat64Array`  
 La sottomatrice restituita da questo metodo.  
  
 `begin`  
 L'indice dell'inizio della matrice.  
  
 `end`  
 L'indice della fine della matrice.  
  
## Note  
 Se `begin` o `end` è negativo, si riferisce a un indice dalla fine della matrice, anziché dall'inizio.  Se `end` non è stato specificato, la sottomatrice contiene tutti gli elementi da `begin` alla fine della matrice tipizzata.  L'intervallo specificato dai valori di `begin` e `end` viene impostato all'intervallo valido degli indici per la matrice corrente.  Se la lunghezza calcolata della nuova matrice tipizzata è negativa, viene impostato a zero.  La matrice restituita è dallo stesso tipo della matrice sulla quale questo metodo è stato invocato.  
  
## Esempio  
 Il seguente esempio mostra come si può ottenere una sottomatrice lunga tre elementi, a partire dal primo elemento della matrice.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var floatArr = new Float64Array(buffer.byteLength / 8);  
            var subArr = floatArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]