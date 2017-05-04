---
title: "Oggetto Uint16Array | Microsoft Docs"
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
ms.assetid: e684647d-04d0-41a9-9089-16612e18ec7d
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Oggetto Uint16Array
Matrice tipizzata di Integer a 16 bit senza segno.  Il contenuto viene inizializzato a 0.  Se il numero di byte richiesti non può essere allocato, viene generata un'eccezione.  
  
## Sintassi  
  
```  
  
      uint16Array = new Uint16Array( length );  
uint16Array = new Uint16Array( array );  
uint16Array = new Uint16Array( buffer, byteOffset, length );  
```  
  
## Parametri  
 `uint16Array`  
 Obbligatorio.  Nome della variabile a cui l'oggetto **Uint16Array** è assegnato.  
  
 `length`  
 Specifica il numero di elementi nella matrice.  
  
 `array`  
 Matrice o matrice tipizzata contenuta in questa matrice.  Il contenuto viene inizializzato in base al contenuto della matrice specificata o della matrice tipizzata, con ogni elemento convertito nel tipo Uint16.  
  
 `buffer`  
 ArrayBuffer rappresentato da Uint16Array.  
  
 `byteOffset`  
 Facoltativa.  Specifica l'offset in byte dall'inizio del buffer da cui deve iniziare Uint16Array.  
  
 `length`  
 Numero di elementi nella matrice.  
  
## Costanti  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Uint16Array`.  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costante BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint16array.md)|Dimensione in byte di ciascun elemento nella matrice.|  
  
## Proprietà  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Uint16Array`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà buffer](../../javascript/reference/buffer-property-uint16array.md)|Solo lettura.  Ottiene l'oggetto ArrayBuffer a cui la matrice fa riferimento.|  
|[Proprietà byteLength](../../javascript/reference/bytelength-property-uint16array.md)|Solo lettura.  Lunghezza della matrice dall'inizio del relativo ArrayBuffer, espressa in byte, fissata in fase di costruzione.|  
|[Proprietà byteOffset](../../javascript/reference/byteoffset-property-uint16array.md)|Solo lettura.  Offset di questa matrice dall'inizio del relativo ArrayBuffer, espresso in byte, fissato in fase di costruzione.|  
|[Proprietà length](../../javascript/reference/length-property-uint16array.md)|Lunghezza della matrice.|  
|||  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Uint16Array`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo set \(Uint16Array\)](../../javascript/reference/set-method-uint16array.md)|Imposta un valore o una matrice di valori.|  
|[Metodo subarray \(Uint16Array\)](../../javascript/reference/subarray-method-uint16array.md)|Ottiene una nuova visualizzazione Uint16Array dell'archivio ArrayBuffer per questa matrice.|  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare un oggetto Uint16Array per elaborare i dati binari acquisiti da XmlHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]