---
title: "Metodo toLocaleTimeString (Date) (JavaScript) | Microsoft Docs"
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
  - "toLocaleTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleTimeString (metodo)"
ms.assetid: 8ad75bf5-864c-4a2a-be90-220e87dce172
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodo toLocaleTimeString (Date) (JavaScript)
Restituisce un'ora come valore di stringa appropriato alle impostazioni locali correnti dell'ambiente host o impostazioni locali specificate.  
  
## Sintassi  
  
```  
  
dateObj.toLocaleTimeString([locales][, options])  
```  
  
#### Parametri  
 `dateObj`  
 Necessario.  Oggetto `Date`.  
  
 `locales`  
 Parametro facoltativo.  Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali.  Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate.  Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate.  
  
 `options`  
 Parametro facoltativo.  Oggetto che contiene una o più proprietà che specificano opzioni di formattazione per la data e l'ora.  
  
## Note  
 A partire da Internet Explorer 11 `toLocaleTimeString` utilizza `Intl.DateTimeFormat` internamente per formattare l'ora, che aggiunge il supporto per la `locales` e `options` parametri.  Per ulteriori informazioni su questi parametri, vedere [intl. DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Il `locales` e `options` parametri non sono supportati in tutte le modalità documento e le versioni del browser.  Per ulteriori informazioni, vedere la sezione Requisiti di sicurezza.  
  
 Quando si utilizza `toLocaleTimeString` in Internet Explorer 10 documento degli standard di modalità, modalità documento precedenti e la modalità non standard:  
  
-   Restituisce un valore stringa che contiene l'ora nel fuso orario corrente.  
  
-   L'ora restituita è nel formato predefinito delle impostazioni locali correnti dell'ambiente host.  
  
 Se si omette il `locales` parametro, il valore restituito di questo metodo non può essere ritenuto scripting, perché cambia a seconda del computer.  In questo scenario, utilizzare il metodo solo al testo in formato di visualizzazione e mai come parte di un calcolo.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `toLocaleTimeString` metodo con opzioni di confronto e delle impostazioni locali specificato.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleTimeString("en-US"));  
document.write(date.toLocaleTimeString("ja-JP"));  
document.write(date.toLocaleTimeString("ar-SA", options));  
document.write(date.toLocaleTimeString("hi-IN", options));  
  
// Output:  
// ‎‎6‎:‎00‎:‎00‎ ‎AM ‎   
// 6‎:‎00‎:‎00‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤ ٠٦‎:‎٠٠‎:‎٠٠‎ ‎ص  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013 06:00:00  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` e `options` parametri:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [Metodo toTimeString \(Date\)](../../javascript/reference/totimestring-method-date-javascript.md)   
 [Metodo toLocaleDateString \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)