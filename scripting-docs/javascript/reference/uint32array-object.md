---
title: "Oggetto Uint32Array | Microsoft Docs"
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
ms.assetid: c4bf5409-2d4b-4660-9f4b-a45d7a02b47e
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Oggetto Uint32Array
Matrice tipizzata di Integer a 32 bit senza segno.  Il contenuto viene inizializzato a 0.  Se il numero di byte richiesti non può essere allocato, viene generata un'eccezione.  
  
## Sintassi  
  
```  
  
      uint32Array = new Uint32Array( length );  
uint32Array = new Uint32Array( array );  
uint32Array = new Uint32Array( buffer, byteOffset, length);  
```  
  
## Parametri  
 `uint32Array`  
 Obbligatorio.  Nome della variabile a cui l'oggetto **Uint32Array** è assegnato.  
  
 `length`  
 Specifica il numero di elementi nella matrice.  
  
 `array`  
 Matrice o matrice tipizzata contenuta in questa matrice.  Il contenuto viene inizializzato in base al contenuto della matrice specificata o della matrice tipizzata, con ogni elemento convertito nel tipo Uint32.  
  
 `buffer`  
 ArrayBuffer rappresentato da Uint32Array.  
  
 `byteOffset`  
 Facoltativa.  Specifica l'offset in byte dall'inizio del buffer da cui deve iniziare Uint32Array.  
  
 `length`  
 Numero di elementi nella matrice.  
  
## Costanti  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Uint32Array`.  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costante BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint32array.md)|Dimensione in byte di ciascun elemento nella matrice.|  
  
## Proprietà  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Uint32Array`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà buffer](../../javascript/reference/buffer-property-uint32array.md)|Solo lettura.  Ottiene l'oggetto ArrayBuffer a cui la matrice fa riferimento.|  
|[Proprietà byteLength](../../javascript/reference/bytelength-property-uint32array.md)|Solo lettura.  Lunghezza della matrice dall'inizio del relativo ArrayBuffer, espressa in byte, fissata in fase di costruzione.|  
|[Proprietà byteOffset](../../javascript/reference/byteoffset-property-uint32array.md)|Solo lettura.  Offset di questa matrice dall'inizio del relativo ArrayBuffer, espresso in byte, fissato in fase di costruzione.|  
|[Proprietà length](../../javascript/reference/length-property-uint32array.md)|Lunghezza della matrice.|  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Uint32Array`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo set \(Uint32Array\)](../../javascript/reference/set-method-uint32array.md)|Imposta un valore o una matrice di valori.|  
|[Metodo subarray \(Uint32Array\)](../../javascript/reference/subarray-method-uint32array.md)|Ottiene una nuova visualizzazione Uint32Array dell'archivio ArrayBuffer per questa matrice.|  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare un oggetto Uint32Array per elaborare i dati binari acquisiti da XMLHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]