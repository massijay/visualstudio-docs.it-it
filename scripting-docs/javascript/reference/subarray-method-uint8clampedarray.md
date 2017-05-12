---
title: "Metodo subarray (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 309ed9e8-5805-47ab-b3ed-501cae1323dd
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo subarray (Uint8ClampedArray)
Ottiene una nuova visualizzazione [Uint8ClampedArray](../../javascript/reference/uint8array-object.md) dell'archivio [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) per questa matrice, specificando il primo e l'ultimo membro della sottomatrice.  
  
## Sintassi  
  
```javascript  
var newUint8ClampedArray = uint8ClampedArray.subarray(begin, end);  
```  
  
## Parametri  
 `newUint8ClampedArray`  
 Obbligatorio.  Sottomatrice restituita da questo metodo.  
  
 `begin`  
 Facoltativo.  Indice dell'inizio della matrice.  
  
 `end`  
 Facoltativo.  Indice della fine della matrice.  Tale indice non è inclusivo.  
  
## Note  
 Se `begin` o `end` è negativo, il valore si riferisce a un indice valutato dalla fine della matrice anziché dall'inizio.  Se `end` non è stato specificato, la sottomatrice contiene tutti gli elementi da `begin` alla fine della matrice tipizzata.  L'intervallo specificato dai valori di `begin` e `end` viene impostato sull'intervallo valido degli indici per la matrice corrente.  Se la lunghezza calcolata della nuova matrice tipizzata è negativa, l'intervallo viene impostato su zero.  La matrice restituita è dello stesso tipo della matrice su cui è stato richiamato questo metodo.  
  
## Esempio  
 Nell'esempio seguente esempio viene mostrato come è possibile ottenere una sottomatrice di due elementi a partire dal primo elemento della matrice.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Vedere anche  
 [Oggetto Uint8Array](../../javascript/reference/uint8array-object.md)   
 [Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)   
 [Oggetto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)