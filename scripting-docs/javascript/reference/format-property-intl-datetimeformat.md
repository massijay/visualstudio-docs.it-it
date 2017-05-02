---
title: "Propriet&#224; format (Intl.DateTimeFormat) | Microsoft Docs"
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Propriet&#224; format (Intl.DateTimeFormat)
Restituisce una funzione che formatta una data specifica delle impostazioni locali utilizzando le impostazioni specificate del formattatore di data\/ora.  
  
## Sintassi  
  
```  
dateTimeFormatObj.format  
```  
  
#### Parametri  
 `dateTimeFormatObj`  
 Necessario.  Il nome dell'oggetto `DateTimeFormat` da utilizzare come formattatore.  
  
## Note  
 La funzione restituita dalla proprietà `format` accetta un singolo argomento, `date`, e restituisce una stringa che rappresenta la data localizzata utilizzando le opzioni specificate nell'oggetto `DateTimeFormat`.  Il parametro `date` della funzione restituita deve essere un numero, una stringa di data o un oggetto `Date`.  Se `date` non viene specificato, tramite la funzione viene utilizzato [Date.now](../../javascript/reference/date-now-function-javascript.md) come valore di input predefinito.  
  
## Esempio  
 Nell'esempio seguente viene utilizzato un oggetto `DateTimeFormat` per localizzare la data "1° dicembre 2007" in tedesco e per riformattarla.  
  
```javascript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [Oggetto Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)