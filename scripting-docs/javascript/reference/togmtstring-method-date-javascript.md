---
title: "Metodo toGMTString (Date) (JavaScript) | Microsoft Docs"
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
  - "toGMTString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toGMTString (metodo)"
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Metodo toGMTString (Date) (JavaScript)
Restituisce una data convertita in una stringa in base all'ora di Greenwich \(GMT, Greenwich Mean Time\).  
  
## Sintassi  
  
```  
  
dateObj.toGMTString()   
```  
  
## Note  
 Il riferimento `dateObj` obbligatorio è un oggetto `Date`.  
  
 Il metodo `toGMTString` è obsoleto e viene fornito solo per la compatibilità con le versioni precedenti.  Si consiglia invece di utilizzare il metodo `toUTCString`.  
  
 Il metodo `toGMTString` restituisce un oggetto `String` contenente la data formattata in base alla convenzione GMT.  Il formato del valore restituito è il seguente: "5 gennaio 1996 00.00.00 GMT".  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo toUTCString \(Date\)](../../javascript/reference/toutcstring-method-date-javascript.md)