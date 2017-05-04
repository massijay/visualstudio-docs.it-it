---
title: "Metodo getHours (Date) (JavaScript) | Microsoft Docs"
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
  - "getHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (oggetto)"
  - "GetHours (metodo)"
  - "Hours (metodo)"
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo getHours (Date) (JavaScript)
Ottiene le ore in una data in base all'ora locale.  
  
## Sintassi  
  
```  
  
dateObj.getHours()   
```  
  
#### Parametri  
 Il riferimento di `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Intero compreso tra 0 e 23 che indica il numero di ore trascorse dalla mezzanotte.  Viene restituito zero se il tempo è precedente a 1:00:00 AM.  Se un oggetto `Date` è stato creato senza specificare l'ora, l'ora sarà per impostazione predefinita uguale a 0.  
  
## Note  
 Per ottenere il valore delle ore in base al formato UTC, utilizza il metodo `getUTCHours`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getHours`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getUTCHours \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Metodo setHours \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [Metodo setUTCHours \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)