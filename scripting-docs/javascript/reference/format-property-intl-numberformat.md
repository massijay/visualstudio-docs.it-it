---
title: "Propriet&#224; format (Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Propriet&#224; format (Intl.NumberFormat)
Restituisce una funzione che formatta un numero specifico delle impostazioni locali utilizzando le impostazioni specificate del formattatore del numero.  
  
## Sintassi  
  
```  
numberFormatObj.format  
```  
  
#### Parametri  
 `numberFormatObj`  
 Necessario.  Il nome dell'oggetto `NumberFormat` da utilizzare come formattatore.  
  
## Note  
 La funzione restituita dalla proprietà `format` accetta un singolo argomento, `value`, e restituisce una stringa che rappresenta il numero localizzato utilizzando le opzioni specificate nell'oggetto `NumberFormat`.  Se `value` non viene fornito, tramite la funzione viene restituito `NaN` \(non un numero\).  
  
## Esempio  
 Nell'esempio seguente viene utilizzato un oggetto `NumberFormat` per creare un numero localizzato.  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [Oggetto Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)