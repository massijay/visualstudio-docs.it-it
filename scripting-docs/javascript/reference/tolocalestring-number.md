---
title: "toLocaleString (Number) | Microsoft Docs"
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toLocaleString (Number)
Converte un numero in una stringa utilizzando le impostazioni locali correnti o specificate.  
  
## Sintassi  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### Parametri  
 `numberObj`  
 Necessario.  Oggetto `Number` da convertire.  
  
 `locales`  
 Opzionale.  Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali.  Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate.  Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate.  
  
 `options`  
 Opzionale.  Oggetto che contiene una o più proprietà che specificano opzioni di confronto.  
  
## Note  
 A partire da Internet Explorer 11, `toLocaleString` utilizza `Intl.NumberFormat` internamente per eseguire confronti, il che costituisce un supporto per i parametri `options` e `locales`.  Per ulteriori informazioni su questi parametri, vedere [Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md).  
  
> [!IMPORTANT]
>  I parametri `options` e `locales` non sono supportati in tutte le modalità di documento e versioni del browser.  Per ulteriori informazioni, vedere la sezione Requisiti.  
  
> [!NOTE]
>  Se si omette il parametro `locales`, utilizzare `toLocaleString` solo per mostrare i risultati a un utente; non utilizzarlo mai per calcolare valori in uno script, poiché il risultato restituito è specifico del computer \(tramite il metodo vengono restituite le impostazioni locali correnti\).  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare il metodo `toLocaleString` senza parametri.  
  
```javascript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## Esempio  
 Di seguito viene illustrato come utilizzare il metodo `toLocaleString` con le impostazioni locali specificate e le opzioni di confronto.  
  
```javascript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Parametri `locales` e `options`  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [Metodo toLocaleDateString \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)