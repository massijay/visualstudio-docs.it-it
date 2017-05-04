---
title: "Oggetto ArrayBuffer | Microsoft Docs"
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Oggetto ArrayBuffer
Rappresenta un buffer non elaborato di dati binari, usato per archiviare i dati per le diverse matrici tipizzate.  Gli oggetti `ArrayBuffers` non possono essere letti o scritti direttamente, ma possono essere passati a una matrice tipizzata o a [Oggetto DataView](../../javascript/reference/dataview-object.md) per interpretare il buffer non elaborato in base alle necessità.  
  
 Per altre informazioni sulle matrici tipizzate, vedere [Matrici tipizzate](../../javascript/advanced/typed-arrays-javascript.md).  
  
## Sintassi  
  
```javascript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## Parametri  
 `arrayBuffer`  
 Obbligatorio.  Nome della variabile a cui l'oggetto `ArrayBuffer` è assegnato.  
  
 `length`  
 La lunghezza del buffer.  I contenuti di ArrayBuffer vengono inizializzati a 0.  Se il numero di byte richiesti non può essere allocato, viene generata un'eccezione.  
  
## Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `ArrayBuffer`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà byteLength](../../javascript/reference/bytelength-property-arraybuffer.md)|Sola lettura.  La lunghezza di ArrayBuffer \(in byte\).|  
  
## Funzioni  
 Nella tabella seguente sono elencate le funzioni dell'oggetto `ArrayBuffer`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[ArrayBuffer.isView Function](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|Determina se un oggetto fornisce una visualizzazione del buffer.|  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `ArrayBuffer`:  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Metodo slice](../../javascript/reference/slice-method-arraybuffer.md)|Restituisce una sezione di un oggetto `ArrayBuffer`.|  
  
## Esempio  
 L'esempio seguente illustra come usare un oggetto ArrayBuffer per elaborare i dati binari acquisiti da [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx).  È possibile usare [Oggetto DataView](../../javascript/reference/dataview-object.md) per ottenere i singoli valori.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Note  
 Per altre informazioni sull'utilizzo di `XmlHttpRequest`, vedere [XMLHttpRequest enhancements](http://msdn.microsoft.com/it-it/be09137c-6546-441b-b953-dcbf72b77069).  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]