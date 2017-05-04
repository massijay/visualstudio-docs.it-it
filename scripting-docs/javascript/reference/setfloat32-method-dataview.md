---
title: "Metodo setFloat32 (DataView) | Microsoft Docs"
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
ms.assetid: b3f68048-c817-48d2-bc17-945e3bcc94d7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo setFloat32 (DataView)
Impostare il valore Float32 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.  Non esiste alcun vincolo di allineamento. I valori a più byte possono essere impostati in corrispondenza di qualsiasi offset.  
  
## Sintassi  
  
```  
dataView.setFloat32 (byteOffset, value, littleEndian);   
```  
  
## Parametri  
 `byteOffset`  
 Posizione nel buffer in corrispondenza della quale recuperare il valore.  
  
 `value`  
 Valore da impostare.  
  
 `littleEndian`  
 Facoltativo.  Se false o non definito, deve essere scritto un valore big\-endian; in caso contrario deve essere scritto un valore little\-endian.  
  
## Note  
 Questi metodi generano un'eccezione in caso di scrittura oltre la fine della visualizzazione.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come impostare il primo valore Float32 di DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setFloat32(0, 9.1);  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]