---
title: "toLocaleString (Date) | Microsoft Docs"
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
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# toLocaleString (Date)
Converte una data in una stringa utilizzando le impostazioni locali correnti o specificate.  
  
## Sintassi  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### Parametri  
 `dateObj`  
 Necessario.  Oggetto `Date` da convertire.  
  
 `locales`  
 Opzionale.  Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali.  Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate.  Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate.  
  
 `options`  
 Opzionale.  Oggetto che contiene una o più proprietà che specificano opzioni di confronto.  
  
## Note  
 A partire da Internet Explorer 11, in `toLocaleString` viene utilizzato l'oggetto `Intl.DateTimeFormat` internamente per l'esecuzione di confronti, tramite cui viene aggiunto il supporto per i parametri `options` e `locales`.  Per ulteriori informazioni su questi parametri, vedere [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  I parametri `options` e `locales` non sono supportati in tutte le modalità di documento e versioni del browser.  Per ulteriori informazioni, vedere la sezione Requisiti.  
  
 Quando si utilizza `toLocaleString` nella modalità documento standard, nelle modalità documento precedenti e nella modalità non standard in Internet Explorer 10:  
  
-   Restituisce un oggetto `String` contenente la data nel formato predefinito esteso delle impostazioni locali correnti.  
  
-   Per le date comprese tra il 1601 e il 1999, la data verrà formattata in base alle impostazioni internazionali specificate nel Pannello di controllo del sistema in uso.  
  
> [!NOTE]
>  Se si omette il parametro `locales`, utilizzare `toLocaleString` solo per mostrare i risultati a un utente; non utilizzarlo mai per calcolare valori in uno script, poiché il risultato restituito è specifico del computer.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `toLocaleString`.  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## Esempio  
 Di seguito viene illustrato come utilizzare il metodo `toLocaleString` con le impostazioni locali specificate e le opzioni di confronto.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Parametri `locales` e `options`  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [Metodo toLocaleDateString \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)