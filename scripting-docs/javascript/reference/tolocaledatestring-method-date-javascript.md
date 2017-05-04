---
title: "Metodo toLocaleDateString (Date) (JavaScript) | Microsoft Docs"
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
  - "toLocaleDateString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleDateString (metodo)"
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Metodo toLocaleDateString (Date) (JavaScript)
Restituisce una data come valore stringa appropriato per le impostazioni locali correnti dell'ambiente host o per le impostazioni locali specificate.  
  
## Sintassi  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### Parametri  
 `dateObj`  
 Necessario.  Un oggetto `Date`.  
  
 `locales`  
 Opzionale.  Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali.  Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate.  Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate.  
  
 `options`  
 Opzionale.  Oggetto che contiene una o più proprietà che specificano opzioni di confronto.  
  
## Note  
 A partire da Internet Explorer 11, in `toLocaleDateString` viene utilizzato l'oggetto `Intl.DateTimeFormat` internamente per formattare la data, tramite cui viene aggiunto il supporto per i parametri `options` e `locales`.  Per ulteriori informazioni su questi parametri, vedere [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  I parametri `options` e `locales` non sono supportati in tutte le modalità di documento e versioni del browser.  Per ulteriori informazioni, vedere la sezione Requisiti.  
  
 Quando si utilizza `toLocaleDateString` nella modalità documento standard, nelle modalità documento precedenti e nella modalità non standard in Internet Explorer 10:  
  
-   Restituisce un valore stringa contenente una data nel fuso orario corrente.  
  
-   La data restituita è nel formato predefinito delle impostazioni locali correnti dell'ambiente host.  
  
 Se si omette il parametro `locales`, il valore restituito da questo metodo non può essere ritenuto attendibile per la creazione di script, in quanto cambia a seconda del computer.  In questo scenario utilizzare il metodo solo per formattare il testo visualizzato, mai come parte di un calcolo.  
  
## Esempio  
 Di seguito viene illustrato come utilizzare il metodo `toLocaleDateString` con le impostazioni locali specificate e le opzioni di confronto.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Parametri `locales` e `options`  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [Metodo toDateString \(Date\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [Metodo toLocaleTimeString \(Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)