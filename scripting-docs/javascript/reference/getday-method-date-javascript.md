---
title: "Metodo getDay (Date) (JavaScript) | Microsoft Docs"
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
  - "getDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetDay (metodo)"
  - "Date (oggetto)"
  - "date, restituzione giorno della settimana"
ms.assetid: 27be7168-3dce-41c9-ae69-6280b7984c2e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Metodo getDay (Date) (JavaScript)
Ottiene il giorno della settimana, utilizzando l'ora locale.  
  
## Sintassi  
  
```  
  
dateObj. getDay()   
```  
  
#### Parametri  
 Il riferimento di `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Intero compreso tra 0 e 6 che rappresenta il giorno della settimana \(domenica corrisponde a 0, sabato a 6\).  
  
## Note  
 Per ottenere il valore del giorno utilizzando il formato UTC \(Universal Coordinated Time, Tempo universale coordinato\), impiegare il metodo `getUTCDay`.  
  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getDay`.  
  
```javascript  
var date = new Date("Saturday, February 9, 2008");  
day = date.getDay();  
document.write(day);  
  
// Output: 6  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getUTCDay \(Date\)](../../javascript/reference/getutcday-method-date-javascript.md)