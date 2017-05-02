---
title: "Metodo getUTCHours (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ore"
  - "ora UTC, restituzione"
  - "getUTCHours (metodo)"
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo getUTCHours (Date) (JavaScript)
Ottiene il valore delle ore in un oggetto `Date` utilizzo di tempo universale coordinato \(UTC\).  
  
## Sintassi  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### Parametri  
 Il riferimento richiesto `dateObj` è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce un Integer compreso tra 0 e 23 che indicano il numero di ore da mezzanotte.  Zero viene restituito se il tempo ha luogo prima a le 1:00: 00 AM.  Se un oggetto `Date` è stato creato senza specificare il tempo, per impostazione predefinita l'ora è 0 in formato UTC.  Questa volta può essere diversa da zero in altri fusi orari.  
  
## Note  
 Per ottenere il numero di ore trascorse dalla mezzanotte in base all'ora locale, è possibile utilizzare il metodo `getHours`.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `getUTCHours`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(datee.getUTCHours());  
  
// Output (in the PST time zone):  
// 8  
// 19  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getHours \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Metodo setHours \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [Metodo setUTCHours \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)