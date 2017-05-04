---
title: "Metodo getMinutes (Date) (JavaScript) | Microsoft Docs"
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
  - "getMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetMinutes (metodo)"
  - "minutes (metodo)"
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo getMinutes (Date) (JavaScript)
Ottiene i minuti di un oggetto `Date` che utilizza l'ora locale.  
  
## Sintassi  
  
```  
  
dateObj.getMinutes()   
```  
  
#### Parametri  
 Il riferimento di `dateObj` obbligatorio è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce un intero compreso tra 0 e 59.  Viene restituito zero quando il valore dell'ora è stato superato da meno di un minuto.  Se un oggetto `Date` è stato creato senza specificare l'ora, il valore dei minuti sarà per impostazione predefinita uguale a 0.  
  
## Note  
 Per ottenere il valore dei minuti utilizzando il formato UTC \(Tempo universale coordinato, Universal Coordinated Time\), è possibile impiegare il metodo `getUTCMinutes`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `getMinutes`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getUTCMinutes \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Metodo setMinutes \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [Metodo setUTCMinutes \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)