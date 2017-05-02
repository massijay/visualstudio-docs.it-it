---
title: "Propriet&#224; number (Error) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Number"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Number (proprietà)"
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Propriet&#224; number (Error) (JavaScript)
Restituisce o imposta il valore numerico associato a uno specifico errore.  La proprietà predefinita dell'oggetto `Error` è **number**.  
  
## Sintassi  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## Parametri  
 *Object*  
 Qualsiasi istanza dell'oggetto `Error`.  
  
 *errorNumber*  
 Integer che rappresenta un errore.  
  
## Note  
 Un numero di errore è un valore a 32 bit.  Il valore a 16 bit di livello superiore è il codice descrittivo, mentre il valore di livello inferiore rappresenta il codice di errore.  Per determinare il codice di errore, utilizzare l'operatore `&` \(And bit per bit\) per combinare la proprietà del numero con il numero esadecimale `0xFFFF`.  
  
## Esempio  
 Nell'esempio seguente viene generata un'eccezione e viene visualizzato il codice di errore derivato dal numero di errore.  
  
```javascript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## Esempio  
 L'output del codice è il seguente.  
  
```javascript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Si applica a**: [Oggetto Error](../../javascript/reference/error-object-javascript.md)  
  
## Vedere anche  
 [Proprietà description \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [Proprietà message \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [Proprietà name \(Error\)](../../javascript/reference/name-property-error-javascript.md)