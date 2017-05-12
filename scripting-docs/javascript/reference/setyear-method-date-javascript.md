---
title: "Metodo setYear (Date) (JavaScript) | Microsoft Docs"
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
  - "setYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setYear (metodo)"
  - "Year (metodo)"
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo setYear (Date) (JavaScript)
Consente di impostare il valore dell'anno nell'oggetto `Date`.  
  
## Sintassi  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## Parametri  
 `dateObj`  
 Obbligatorio.  Qualsiasi oggetto `Date`.  
  
 `numYear`  
 Obbligatorio.  Per gli anni compresi tra 1900 e 1999, rappresenta un valore numerico uguale all'anno meno 1900.  Per le date non comprese nell'intervallo, è un valore numerico a 4 cifre.  
  
## Note  
 Questo metodo è obsoleto e viene mantenuto solo per la compatibilità con le versioni precedenti.  In alternativa, utilizzare il metodo `setFullYear`.  
  
 Per impostare l'anno di un oggetto `Date` su 1997, chiamare **setYear\(97\)**.  Per impostare l'anno su 2010, chiamare **setYear\(2010\)**.  Per impostare infine l'anno su un valore compreso nell'intervallo tra 0 e 99, utilizzare il metodo `setFullYear`.  
  
> [!NOTE]
>  In [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 1.0 `setYear` utilizza un valore che è il risultato della somma di 1900 al valore dell'anno specificato in `numYear`, indipendentemente dal valore dell'anno.  Ad esempio, per impostare l'anno su 1899, `numYear` è \-1, mentre per impostare l'anno su 2000, `numYear` è 100.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getFullYear \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Metodo getUTCFullYear \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Metodo getYear \(Date\)](../../javascript/reference/getyear-method-date-javascript.md)   
 [Metodo setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Metodo setUTCFullYear \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)