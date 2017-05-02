---
title: "Metodo toISOString (Date) (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "toISOString (metodo) [JavaScript]"
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Metodo toISOString (Date) (JavaScript)
Restituisce una data come valore stringa in formato ISO.  
  
## Sintassi  
  
```javascript  
  
objDate.toISOString()  
```  
  
## Valore restituito  
 Rappresentazione in forma di stringa della data in formato ISO \(International Organization for Standardization\).  
  
## Eccezioni  
 Se `objDate` non contiene una data valida, viene generata un'eccezione `RangeError`.  
  
## Note  
 Il formato ISO è una semplificazione del formato ISO 8601.  Per ulteriori informazioni, vedi [Stringhe di data e ora](../../javascript/date-and-time-strings-javascript.md).  
  
 Il fuso orario è sempre UTC, indicato dal suffisso Z nell'output.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `toISOString`.  
  
```javascript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Oggetto Date](../../javascript/reference/date-object-javascript.md)   
 [Stringhe di data e ora](../../javascript/date-and-time-strings-javascript.md)