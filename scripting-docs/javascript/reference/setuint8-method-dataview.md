---
title: "Metodo setUint8 (DataView) | Microsoft Docs"
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
ms.assetid: b294262b-3f4b-4183-a292-5a6982cbdd27
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo setUint8 (DataView)
Archivia un valore Uint8 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.  
  
## Sintassi  
  
```  
dataView.setUint8(byteOffset, value);   
```  
  
## Parametri  
 `byteOffset`  
 Posizione nel buffer in corrispondenza della quale impostare il valore.  
  
 `value`  
 Valore da impostare.  
  
## Note  
 Questi metodi generano un'eccezione in caso di scrittura oltre la fine della visualizzazione.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come impostare il primo valore Uint8 di DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint8(0, 9);  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]