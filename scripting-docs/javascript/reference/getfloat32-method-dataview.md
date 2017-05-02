---
title: "Metodo getFloat32 (DataView) | Microsoft Docs"
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
ms.assetid: adecf671-bde4-46be-a875-33b6d6e970b1
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo getFloat32 (DataView)
Ottiene il valore Float32 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.  Non esiste alcun vincolo di allineamento. I valori a più byte possono essere recuperati da qualsiasi offset.  
  
## Sintassi  
  
```  
var testFloat = dataView.getFloat32(byteOffset, littleEndian);   
```  
  
## Parametri  
 `testFloat`  
 Obbligatorio.  Valore Float32 restituito dal metodo.  
  
 `byteOffset`  
 Posizione nel buffer in corrispondenza della quale recuperare il valore.  
  
 `littleEndian`  
 Facoltativo.  Se false o non definito, deve essere letto un valore big\-endian; in caso contrario deve essere letto un valore little\-endian.  
  
## Note  
 Questi metodi generano un'eccezione in caso di lettura oltre la fine della visualizzazione.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come ottenere il primo valore Float32 di DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getFloat32(0));  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]