---
title: "Metodo setUint16 (DataView) | Microsoft Docs"
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
ms.assetid: bdf47cda-7fa5-4aaa-8aa2-8cf9a8d56cb3
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo setUint16 (DataView)
Imposta il valore Uint16 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.  Non esiste alcun vincolo di allineamento. I valori a più byte possono essere impostati in corrispondenza di qualsiasi offset.  
  
## Sintassi  
  
```  
dataView.setUint16(byteOffset, value, littleEndian);   
```  
  
## Parametri  
 `testInt`  
 Obbligatorio.  Valore Uint16 restituito dal metodo.  
  
 `value`  
 Valore da impostare.  
  
 `byteOffset`  
 Posizione nel buffer in corrispondenza della quale recuperare il valore.  
  
 `littleEndian`  
 Facoltativo.  Se false o non definito, deve essere scritto un valore big\-endian; in caso contrario deve essere scritto un valore little\-endian.  
  
## Note  
 Questi metodi generano un'eccezione in caso di scrittura oltre la fine della visualizzazione.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come impostare il primo valore Uint16 di DataView.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint16(0, 9);  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]