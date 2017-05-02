---
title: "Oggetto Float64Array | Microsoft Docs"
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
ms.assetid: 74c945dc-56ae-458c-b0aa-782f240e9b6c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Oggetto Float64Array
Matrice tipizzata di valori float a 64 bit.  Il contenuto viene inizializzato a 0.  Se il numero di byte richiesti non può essere allocato, viene generata un'eccezione.  
  
## Sintassi  
  
```  
  
float64Array = new Float64Array( length ); float64Array = new Float64Array( array ); float64Array = new Float64Array( buffer, byteOffset, length);  
```  
  
## Parametri  
 `float64Array`  
 Obbligatorio.  Nome della variabile a cui l'oggetto **Float64Array** è assegnato.  
  
 `length`  
 Specifica il numero di elementi nella matrice.  
  
 `array`  
 Matrice o matrice tipizzata contenuta in questa matrice.  Il contenuto viene inizializzato in base al contenuto della matrice specificata o della matrice tipizzata, con ogni elemento convertito nel tipo Float64.  
  
 `buffer`  
 ArrayBuffer rappresentato da Float64Array.  
  
 `byteOffset`  
 Facoltativo.  Specifica l'offset in byte dall'inizio del buffer da cui deve iniziare Float64Array.  
  
 `length`  
 Numero di elementi nella matrice.  
  
## Costanti  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Float64Array`.  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costante BYTES\_PER\_ELEMENT](../../javascript/reference/bytes-per-element-constant-float64array.md)|Dimensione in byte di ogni elemento nella matrice.|  
  
## Proprietà  
 Nella tabella seguente sono elencate le costanti dell'oggetto `Float64Array`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà buffer](../../javascript/reference/bytelength-property-float64array.md)|Sola lettura.  Ottiene l'oggetto ArrayBuffer a cui la matrice fa riferimento.|  
|[Proprietà byteLength](../../javascript/reference/bytelength-property-float64array.md)|Sola lettura.  Lunghezza della matrice dall'inizio del relativo ArrayBuffer, espressa in byte, fissata in fase di costruzione.|  
|[Proprietà byteOffset](../../javascript/reference/length-property-float64array.md)|Sola lettura.  Offset di questa matrice dall'inizio del relativo ArrayBuffer, espresso in byte, fissato in fase di costruzione.|  
|[Proprietà length](../../javascript/reference/length-property-float64array.md)|Lunghezza della matrice.|  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Float64Array`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo get](../../javascript/reference/get-method-float64array.md)|Può essere omesso.  Ottiene l'elemento in corrispondenza dell'indice specificato.|  
|[Metodo set \(Float64Array\)](../../javascript/reference/set-method-float64array.md)|Imposta un valore o una matrice di valori.|  
|[Metodo subarray \(Float64Array\)](../../javascript/reference/subarray-method-float64array.md)|Ottiene una nuova visualizzazione Float64Array dell'archivio ArrayBuffer per questa matrice.|  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare un oggetto Float64Array per elaborare i dati binari acquisiti da XmlHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float64Array(buffer.byteLength / 8);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat64(i * 8);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]