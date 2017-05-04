---
title: "Matrici tipizzate (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: fa82c562-0ebf-4559-aecc-166e59f7fb64
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Matrici tipizzate (JavaScript)
È possibile usare matrici tipizzate per gestire dati binari da origini come protocolli di rete, formati di file binari e buffer di grafica non elaborata.  Le matrici tipizzate possono essere usate anche per gestire dati binari in memoria con layout di byte noti.  
  
## Esempio  
 Il codice seguente mostra come usare un [Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) come risposta di un oggetto [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx).  È possibile modificare i byte nella risposta usando i diversi metodi dell'[Oggetto DataView](../../javascript/reference/dataview-object.md) oppure copiando i byte nella matrice tipizzata appropriata.  
  
> [!TIP]
>  Per altre informazioni sull'uso di tipi di risposta diversi con un oggetto `XmlHttpRequest`, vedere [XMLHttpRequest.responseType](http://msdn.microsoft.com/it-it/8d7738d1-4bfd-4cf1-8015-174def089556), [Miglioramenti a XMLHttpRequest](http://msdn.microsoft.com/it-it/be09137c-6546-441b-b953-dcbf72b77069) e [Download di diversi tipi di contenuto \(app di Windows Store\)](http://msdn.microsoft.com/it-it/c0006bbd-17f9-4c6a-af81-2acaf109111d).  
  
```javascript  
...  
<div id="xhrDiv"></div>  
...  
var name = "http://www.microsoft.com";  
var xhrDiv = document.getElementById("xhrDiv");  
  
var req = new XMLHttpRequest();  
req.open("GET", name, true);  
req.responseType = "arraybuffer";  
req.onreadystatechange = function () {  
if (req.readyState == req.DONE) {  
    var arrayResponse = req.response;  
    var dataView = new DataView(arrayResponse);  
    var ints = new Uint32Array(dataView.byteLength / 4);  
  
    xhrDiv.style.backgroundColor = "#00FF00";  
    xhrDiv.innerText = "Array is " + ints.length + "uints long";  
    }  
}  
req.send();  
```  
  
## ArrayBuffer  
 Un [Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) rappresenta un buffer di dati non elaborati usato per archiviare dati per diverse matrici tipizzate.  Non è possibile leggere o scrivere in un oggetto `ArrayBuffer`, ma è possibile passarlo a una matrice tipizzata o a un oggetto [Oggetto DataView](../../javascript/reference/dataview-object.md) per interpretare il buffer di dati non elaborati.  È possibile usare un oggetto `ArrayBuffer` per archiviare qualsiasi tipo di dati \(o tipi misti di dati\).  
  
## DataView  
 È possibile usare un [Oggetto DataView](../../javascript/reference/dataview-object.md) per leggere e scrivere i diversi tipi di dati binari in qualsiasi posizione nell'oggetto `ArrayBuffer`.  
  
## Matrici tipizzate  
 I tipi di matrice tipizzata rappresentano le visualizzazioni di un [Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) che può essere indicizzato e modificato.  Tutti i tipi di matrice sono di lunghezza fissa.  
  
||||  
|-|-|-|  
|Nome|Dimensioni \(in byte\)|Descrizione|  
|[Oggetto Int8Array](../../javascript/reference/int8array-object.md)|1|Intero con segno in complemento a due a 8 bit|  
|[Oggetto Uint8Array](../../javascript/reference/uint8array-object.md)|1|Intero senza segno a 8 bit|  
|[Oggetto Int16Array](../../javascript/reference/int16array-object.md)|2|Intero con segno in complemento a due a 16 bit|  
|[Oggetto Uint16Array](../../javascript/reference/uint16array-object.md)|2|Intero senza segno a 16 bit|  
|[Oggetto Int32Array](../../javascript/reference/int32array-object.md)|4|Intero con segno in complemento a due a 32 bit|  
|[Oggetto Uint32Array](../../javascript/reference/uint32array-object.md)|4|Intero senza segno a 32 bit|  
|[Oggetto Float32Array](../../javascript/reference/float32array-object.md)|4|Numero a virgola mobile IEE a 32 bit|  
|[Oggetto Float64Array](../../javascript/reference/float64array-object.md)|8|Numero a virgola mobile IEE a 64 bit|