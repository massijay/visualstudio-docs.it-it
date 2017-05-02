---
title: "Metodo set (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 1298443d-5c4c-4329-9ad2-35e213dca157
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo set (Uint8ClampedArray)
Imposta un valore o una matrice di valori.  
  
## Sintassi  
  
```javascript  
uint8ClampedArray.set(index, value); uint8ClampedArray.set(array, offset);   
```  
  
## Parametri  
 `index`  
 Indice della posizione da impostare.  
  
 `value`  
 Valore da impostare.  
  
 `array`  
 Matrice tipizzata o non tipizzata di valori da impostare.  
  
 `offset`  
 Indice nella matrice corrente in base al quale devono essere scritti i valori.  
  
## Note  
 Se la matrice di input è una matrice tipizzata, le due matrici possono utilizzare lo stesso oggetto [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) sottostante.  In questa situazione l'impostazione dei valori viene eseguita come se tutti i dati fossero stati prima copiati in un buffer temporaneo che non si sovrappone ad alcuna matrice e come se successivamente i dati presenti nel buffer temporaneo venissero copiati nella matrice corrente.  
  
 Se il valore ottenuto sommando l'offset e la lunghezza della matrice specificata non è compreso nell'intervallo per la matrice tipizzata corrente, viene generata un'eccezione.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come impostare il primo elemento della matrice.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Vedere anche  
 [Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)   
 [Oggetto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)