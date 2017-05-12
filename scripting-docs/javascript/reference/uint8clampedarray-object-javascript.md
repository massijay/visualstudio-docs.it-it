---
title: "Oggetto Uint8ClampedArray (JavaScript) | Microsoft Docs"
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
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Oggetto Uint8ClampedArray (JavaScript)
Matrice tipizzata di valori Unsigned Integer a 8 bit con valori fissati sull'intervallo 0\-255.  Il contenuto viene inizializzato a 0.  Se non è possibile allocare il numero di byte richiesto, viene generata un'eccezione.  
  
## Sintassi  
  
```  
  
uint8ClampedArray = new Uint8ClampedArray( length ); uint8ClampedArray = new Uint8ClampedArray( array ); uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## Parametri  
 `uint8ClampedArray`  
 Obbligatorio.  Nome della variabile a cui l'oggetto `Uint8ClampedArray` è assegnato.  
  
 `length`  
 Facoltativo.  Numero di elementi nella matrice.  
  
 `array`  
 Facoltativo.  Matrice o matrice tipizzata contenuta in questa matrice.  Il contenuto viene inizializzato in base al contenuto della matrice specificata o della matrice tipizzata, con ogni elemento convertito nel tipo `Uint8`.  
  
 `buffer`  
 Facoltativo.  [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) rappresentato da `Uint8ClampedArray`.  
  
 `byteOffset`  
 Facoltativo.  Offset in byte dall'inizio del buffer da cui deve iniziare `Uint8ClampedArray`.  
  
 `length`  
 Facoltativo.  Numero di elementi nella matrice.  
  
## Note  
 I valori archiviati in un oggetto `Uint8ClampedArray` sono compresi tra 0 e 255.  Se si imposta un valore negativo per un membro di matrice, il valore impostato è 0.  Se si imposta un valore maggiore di 255, il valore impostato è 255.  
  
 I valori in un oggetto `Uint8ClampedArray` vengono arrotondati al valore di evento più vicino, noto come arrotondamento al numero pari più vicino.  
  
## Costanti  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Uint8ClampedArray`.  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costante BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|Dimensione in byte di ogni elemento nella matrice.|  
  
## Proprietà  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Uint8ClampedArray`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà buffer](../../javascript/reference/buffer-property-uint8clampedarray.md)|Sola lettura.  Ottiene l'oggetto [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) a cui la matrice fa riferimento.|  
|[Proprietà byteLength](../../javascript/reference/bytelength-property-uint8clampedarray.md)|Sola lettura.  Lunghezza della matrice dall'inizio del relativo [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), espressa in byte, fissata in fase di costruzione.|  
|[Proprietà byteOffset](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|Sola lettura.  Offset di questa matrice dall'inizio del relativo [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), espresso in byte, fissato in fase di costruzione.|  
|[Proprietà length](../../javascript/reference/length-property-uint8clampedarray.md)|Lunghezza della matrice.|  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Uint8ClampedArray`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo set](../../javascript/reference/set-method-uint8clampedarray.md)|Imposta un valore o una matrice di valori.|  
|[Metodo subarray](../../javascript/reference/subarray-method-uint8clampedarray.md)|Ottiene una nuova visualizzazione `Uint8ClampedArray` dell'archivio [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) per questa matrice, specificando il primo e l'ultimo elemento della sottomatrice.|  
  
## Esempio  
 L'esempio seguente mostra come usare un oggetto `Uint8ClampedArray` per elaborare i dati binari acquisiti da `XmlHttpRequest`:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8ClampedArray(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Esempio  
 L'esempio seguente mostra in che modo i valori vengono limitati in `Uint8ClampedArray`.  
  
```javascript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## Esempio  
 L'esempio seguente mostra in che modo i valori vengono arrotondati in `Uint8ClampedArray`.  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 11 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Vedere anche  
 [Oggetto Uint8Array](../../javascript/reference/uint8array-object.md)   
 [Oggetto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)