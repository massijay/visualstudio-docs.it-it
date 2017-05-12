---
title: "Metodo set (Float32Array) | Microsoft Docs"
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
ms.assetid: 0d486ed3-72eb-4af2-b0a6-ae727c588883
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Metodo set (Float32Array)
Imposta un valore o una matrice di valori.  
  
## Sintassi  
  
```javascript  
float32Array.set(index, value);  
float32Array.set(array, offset);  
  
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
 Se la matrice di input è un oggetto TypedArray, le due matrici possono utilizzare lo stesso oggetto ArrayBuffer sottostante.  In questa situazione, l'impostazione dei valori viene eseguita come se tutti i dati venissero prima copiati in un buffer temporaneo che non si sovrappone ad alcuna matrice e come se successivamente i dati presenti nel buffer temporaneo venissero copiati nella matrice corrente.  
  
 Se l'offset più la lunghezza della matrice specificata non è compreso nell'intervallo per l'oggetto TypedArray corrente, viene generata un'eccezione.  
  
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
            var floatArr = new Float32Array(buffer.byteLength / 4);  
            floatArr.set(0, 9);  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]