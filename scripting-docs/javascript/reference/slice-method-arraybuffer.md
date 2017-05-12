---
title: "Metodo slice (ArrayBuffer) | Microsoft Docs"
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo slice (ArrayBuffer)
Restituisce una sezione di un oggetto [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## Sintassi  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## Parametri  
 `arrayBufferObj`  
 Obbligatorio.  Oggetto [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) da cui verrà copiata la sezione.  
  
 `start`  
 Obbligatorio.  Indice byte dell'inizio della sezione da copiare.  
  
 `end`  
 Facoltativo.  Indice byte della fine della sezione da copiare.  
  
## Note  
 Il metodo `slice` restituisce un oggetto [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) che contiene la parte specificata di `arrayBufferObj`.  
  
 Il metodo `slice` copia, senza includerlo, fino al byte indicato da `end`.  Se `start` o `end` è negativo, l'indice specificato viene considerato rispettivamente come la somma di `length` e `start` o `end`, in cui `length` è la lunghezza dell'oggetto [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  Se `end` viene omesso, l'estrazione continua fino alla fine di `arrayBufferObj`.  Se `end` si verifica prima di `start`, non vengono copiati byte nel nuovo oggetto [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## Esempio  
 Gli esempi seguenti mostrano come usare il metodo `slice`.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## Requisiti  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Vedere anche  
 [Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)