---
title: "Oggetto Int16Array | Microsoft Docs"
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
ms.assetid: b87f36b4-4e38-4f32-b258-654c4ad2c615
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Oggetto Int16Array
Matrice tipizzata di Integer a 16 bit.  Il contenuto viene inizializzato a 0.  Se il numero di byte richiesti non può essere allocato, viene generata un'eccezione.  
  
## Sintassi  
  
```  
  
      int16Array = new Int16Array( length );  
int16Array = new Int16Array( array );  
int16Array = new Int16Array( buffer, byteOffset, length);  
```  
  
## Parametri  
 `int16Array`  
 Obbligatorio.  Nome della variabile a cui l'oggetto **Int16Array** è assegnato.  
  
 `length`  
 Specifica il numero di elementi nella matrice.  
  
 `array`  
 Matrice o matrice tipizzata contenuta in questa matrice.  Il contenuto viene inizializzato in base al contenuto della matrice specificata o della matrice tipizzata, con ogni elemento convertito nel tipo Int16.  
  
 `buffer`  
 ArrayBuffer rappresentato da Int16Array.  
  
 `byteOffset`  
 Facoltativa.  Specifica l'offset in byte dall'inizio del buffer da cui deve iniziare Int16Array.  
  
 `length`  
 Numero di elementi nella matrice.  
  
## Costanti  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Int16Array`.  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costante BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-int16array.md)|Dimensione in byte di ciascun elemento nella matrice.|  
  
## Proprietà  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Int16Array`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà buffer](../../javascript/reference/buffer-property-int16array.md)|Solo lettura.  Ottiene l'oggetto ArrayBuffer a cui la matrice fa riferimento.|  
|[Proprietà byteLength](../../javascript/reference/byteoffset-property-int16array.md)|Solo lettura.  Lunghezza della matrice dall'inizio del relativo ArrayBuffer, espressa in byte, fissata in fase di costruzione.|  
|[Proprietà byteOffset](../../javascript/reference/byteoffset-property-int16array.md)|Solo lettura.  Offset di questa matrice dall'inizio del relativo ArrayBuffer, espresso in byte, fissato in fase di costruzione.|  
|[Proprietà length](../../javascript/reference/length-property-int16array.md)|Lunghezza della matrice.|  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Int16Array`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo set \(Int16Array\)](../../javascript/reference/set-method-int16array.md)|Imposta un valore o una matrice di valori.|  
|[Metodo subarray \(Int16Array\)](../../javascript/reference/subarray-method-int16array.md)|Ottiene una nuova visualizzazione Int16Array dell'archivio ArrayBuffer per questa matrice.|  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare un oggetto Int16Array per elaborare i dati binari acquisiti da XmlHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]