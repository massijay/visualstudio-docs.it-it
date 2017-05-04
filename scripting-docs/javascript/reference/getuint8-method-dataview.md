---
title: "Metodo getUint8 (DataView) | Microsoft Docs"
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
ms.assetid: 9fbf4be3-4c0b-4963-a7a1-d57f1501b4cf
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo getUint8 (DataView)
Ottiene il valore Uint8 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.  Non esiste alcun vincolo di allineamento. I valori a più byte possono essere recuperati da qualsiasi offset.  
  
## Sintassi  
  
```  
var testInt = dataView.getUint8(byteOffset);   
```  
  
## Parametri  
 `testInt`  
 Obbligatorio.  Valore Uint8 restituito dal metodo.  
  
 `byteOffset`  
 Posizione nel buffer in corrispondenza della quale recuperare il valore.  
  
## Note  
 Questi metodi generano un'eccezione in caso di lettura oltre la fine della visualizzazione.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come ottenere il primo valore Uint8 di DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getUint8(0));  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]