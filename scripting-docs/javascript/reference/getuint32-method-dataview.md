---
title: "Metodo getUint32 (DataView) | Microsoft Docs"
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
ms.assetid: 266ee6b6-c0b6-417e-a64b-c8cda48fde86
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo getUint32 (DataView)
Ottiene il valore Uint32 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.  Non esiste alcun vincolo di allineamento. I valori a più byte possono essere recuperati da qualsiasi offset.  
  
## Sintassi  
  
```  
var testInt = dataView.get Uint32 (byteOffset, littleEndian);   
```  
  
## Parametri  
 `testInt`  
 Obbligatorio.  Valore Uint32 restituito dal metodo.  
  
 `byteOffset`  
 Posizione nel buffer in corrispondenza della quale recuperare il valore.  
  
 `littleEndian`  
 Facoltativo.  Se false o non definito, deve essere letto un valore big\-endian; in caso contrario deve essere letto un valore little\-endian.  
  
## Note  
 Questi metodi generano un'eccezione in caso di lettura oltre la fine della visualizzazione.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come ottenere il primo valore Uint32 di DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getUint32(0));  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]