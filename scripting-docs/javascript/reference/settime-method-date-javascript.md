---
title: "Metodo setTime (Date) (JavaScript) | Microsoft Docs"
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
  - "setTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "SetTime (metodo)"
  - "time (metodo)"
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Metodo setTime (Date) (JavaScript)
Imposta il valore di data e ora nell'oggetto `Date`.  
  
## Sintassi  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 *milliseconds*  
 Obbligatorio.  Valore numerico che rappresenta il numero di millisecondi trascorsi dalla mezzanotte dell'1 gennaio 1970 espressa in formato GMT.  
  
## Note  
 Se *milliseconds* è un numero negativo, viene indicata una data precedente al 1970.  L'intervallo approssimativo di date disponibili è compreso tra 285.616 anni prima e 285.616 anni dopo il 1970.  
  
 L'impostazione di data e ora con il metodo `setTime` non dipende dal fuso orario.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `setTime`.  
  
```javascript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getTime \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)