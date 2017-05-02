---
title: "Oggetto DataView | Microsoft Docs"
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Oggetto DataView
È possibile utilizzare un oggetto DataView per leggere e scrivere i diversi tipi di dati binari in qualsiasi posizione di ArrayBuffer.  
  
## Sintassi  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## Parametri  
 `dataView`  
 Necessario.  Nome della variabile a cui l'oggetto **DataView** è assegnato.  
  
 `buffer`  
 ArrayBuffer rappresentato da DataView.  
  
 `byteOffset`  
 Opzionale.  Specifica l'offset in byte dall'inizio del buffer da cui deve iniziare DataView.  
  
 `byteLength`  
 Opzionale.  Specifica la lunghezza \(in byte\) della sezione del buffer che l'oggetto DataView deve rappresentare.  
  
## Note  
 Se byteOffset e byteLength vengono omessi, DataView si estende sull'intero intervallo di ArrayBuffer.  Se byteLength viene omesso, DataView si estende dal parametro byteOffset specificato fino alla fine di ArrayBuffer.  Se i parametri byteOffset e byteLength specificati fanno riferimento a un'area oltre la fine di ArrayBuffer, viene generata un'eccezione.  
  
## Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `DataView`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà buffer](../../javascript/reference/buffer-property-dataview.md)|Solo lettura.  Ottiene l'oggetto ArrayBuffer a cui la visualizzazione fa riferimento.|  
|[Proprietà byteLength](../../javascript/reference/bytelength-property-dataview.md)|Solo lettura.  Lunghezza della visualizzazione dall'inizio di ArrayBuffer, in byte, corretta in fase di costruzione.|  
|[Proprietà byteOffset](../../javascript/reference/byteoffset-property-dataview.md)|Solo lettura.  Offset della visualizzazione dall'inizio del relativo ArrayBuffer, in byte, corretto in fase di costruzione.|  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `DataView`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo getInt8](../../javascript/reference/getint8-method-dataview.md)|Ottiene il valore Int8 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo getUint8 \(DataView\)](../../javascript/reference/getuint8-method-dataview.md)|Ottiene il valore Uint8 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo getInt16 \(DataView\)](../../javascript/reference/getint16-method-dataview.md)|Ottiene il valore Int16 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo getUint16 \(DataView\)](../../javascript/reference/getuint16-method-dataview.md)|Ottiene il valore Uint16 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo getInt32 \(DataView\)](../../javascript/reference/getint32-method-dataview.md)|Ottiene il valore Int32 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo getUint32 \(DataView\)](../../javascript/reference/getuint32-method-dataview.md)|Ottiene il valore Uint32 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo getFloat32 \(DataView\)](../../javascript/reference/getfloat32-method-dataview.md)|Ottiene il valore Float32 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo getFloat64 \(DataView\)](../../javascript/reference/getfloat64-method-dataview.md)|Ottiene il valore Float64 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo setInt8 \(DataView\)](../../javascript/reference/setint8-method-dataview.md)|Archivia un valore Int8 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo setUint8 \(DataView\)](../../javascript/reference/setuint8-method-dataview.md)|Archivia un valore Uint8 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo setInt16 \(DataView\)](../../javascript/reference/setint16-method-dataview.md)|Archivia un valore Int16 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo setUint16 \(DataView\)](../../javascript/reference/setuint16-method-dataview.md)|Archivia un valore Uint16 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo setInt32 \(DataView\)](../../javascript/reference/setint32-method-dataview.md)|Archivia un valore Int32 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo setUint32 \(DataView\)](../../javascript/reference/setuint32-method-dataview.md)|Archivia un valore Uint32 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo setFloat32 \(DataView\)](../../javascript/reference/setfloat32-method-dataview.md)|Archivia un valore Float32 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
|[Metodo setFloat64 \(DataView\)](../../javascript/reference/setfloat64-method-dataview.md)|Archivia un valore Float64 in corrispondenza dell'offset di byte specificato dall'inizio della visualizzazione.|  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare un oggetto DataView per elaborare i dati binari acquisiti da XmlHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var ints = new Int32Array(dataView.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]