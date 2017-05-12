---
title: "Metodo toLocaleString (Object) (JavaScript) | Microsoft Docs"
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
  - "toLocaleString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleString (metodo)"
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Metodo toLocaleString (Object) (JavaScript)
Restituisce una data convertita in una stringa in base alle impostazioni locali correnti.  
  
## Sintassi  
  
```  
  
dateObj.toLocaleString()   
```  
  
## Note  
 L'argomento `dateObj` obbligatorio corrisponde a qualsiasi oggetto `Date`.  
  
 Il metodo `toLocaleString` restituisce un oggetto `String` contenente la data nel formato predefinito esteso delle impostazioni locali correnti.  
  
-   Per le date comprese tra il 1601 e il 1999 d.C., la data viene formattata in base alle impostazioni internazionali specificate nel Pannello di controllo del sistema in uso.  
  
-   Per le date non comprese in questo intervallo, viene utilizzato il formato predefinito del metodo **toString**.  
  
 Negli Stati Uniti, ad esempio, `toLocaleString` restituisce "01\/05\/96 00:00:00" per il 5 gennaio.  In Europa restituisce "05\/01\/96 00.00.00" per la stessa data, poiché in base alla convenzione europea il giorno viene inserito prima del mese.  
  
> [!NOTE]
>  Il metodo `toLocaleString` deve essere utilizzato solo per visualizzare i risultati e mai come base di calcolo all'interno di uno script in quanto il risultato restituito è specifico del computer.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `toLocaleString`.  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Array](../../javascript/reference/array-object-javascript.md)&#124; [Oggetto Date](../../javascript/reference/date-object-javascript.md)&#124; [Oggetto Number](../../javascript/reference/number-object-javascript.md)&#124; [Oggetto Object](../../javascript/reference/object-object-javascript.md)  
  
## Vedere anche  
 [Metodo toLocaleDateString \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)