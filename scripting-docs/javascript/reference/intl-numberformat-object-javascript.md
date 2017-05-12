---
title: "Oggetto Intl.NumberFormat (JavaScript) | Microsoft Docs"
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
  - "NumberFormat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Oggetto Intl.NumberFormat (JavaScript)
Fornisce la formattazione di numeri specifica delle impostazioni locali.  
  
## Sintassi  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### Parametri  
 `numberFormatObj`  
 Necessario.  Il nome della variabile a cui assegnare l'oggetto `NumberFormat`.  
  
 `locales`  
 Opzionale.  Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali.  Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate.  Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate.  Per ulteriori informazioni vedere la sezione Osservazioni.  
  
 `options`  
 Opzionale.  Oggetto che contiene una o più proprietà che specificano opzioni di formattazione dei numeri.  Per ulteriori informazioni, vedere la sezione relativa alle note.  
  
## Note  
 Il parametro `locales` deve rispettare il linguaggio [BCP 47](http://tools.ietf.org/html/rfc5646) o i tag per le impostazioni locali come "en\-US" e "zh\-cn".  Il tag può includere il linguaggio, l'area, il paese e il variant.  Per esempi di tag di lingua, vedere l'[Appendice A](http://tools.ietf.org/html/rfc5646#appendix-A) di BCP 47.  Per `NumberFormat`, è possibile aggiungere il sottotag **\-u** seguito da \-nu per specificare un'estensione del sistema di numerazione:  
  
 "*language*\-*region*\-u\-nu\-*numberingsystem*"  
  
 dove *numberingsystem* può essere: arab, arabext, bali, beng, deva, fullwide, gujr, guru, hanidec, khmr, knda, laoo, latn, limb, mylm, mong, mymr, orya, tamldec, telu, thai e tibt.  
  
 Il parametro `options` può includere le seguenti proprietà:  
  
|Proprietà|Descrizione|Valori possibili|Valore predefinito|  
|---------------|-----------------|----------------------|------------------------|  
|`localeMatcher`|Specifica l'algoritmo di corrispondenza delle impostazioni locali da utilizzare.|"lookup", "best fit"|"best fit"|  
|`style`|Specifica lo stile del formato del numero.|"decimal", "percent", "currency"|"decimale"|  
|`currency`|Specifica il valore di valuta ISO 4217 come codice alfabetico.  Se `style` è impostato su "valuta", questo valore è obbligatorio.|Vedere l'[elenco di codici di valute e fondi](http://www.currency-iso.org/en/home/tables/table-a1.html) ISO.|undefined|  
|`currencyDisplay`|Specifica se visualizzare la valuta come codice valuta alfabetico ISO 4217 o nome o simbolo di valuta localizzato.  Questo valore viene utilizzato solo se `style` è impostato su "valuta".|"code", "symbol", "name"|"simbolo"|  
|`useGrouping`|Specifica se un separatore di raggruppamento deve essere utilizzato.|true, false|`true`.|  
|`minimumIntegerDigits`|Specifica il numero minimo di cifre intere da utilizzare.|da 1 a 21.|21|  
|`minimumFractionDigits`|.  Specifica il numero minimo di cifre frazionarie da utilizzare.|da 0 a 20.|0|  
|`maximumFractionDigits`|Specifica il numero massimo di cifre frazionarie da utilizzare.|Questo valore può essere compreso tra `minimumFractionDigits` e 20.|20.|  
|`minimumSignificantDigits`|Specifica il numero minimo di cifre frazionarie da visualizzare.|Questo valore può essere compreso tra 1 e 21.|1|  
|`maximumSignificantDigits`|Specifica il numero massimo di cifre frazionarie da visualizzare.|Questo valore può essere compreso tra `minimumSignificantDigits` e 21.|21|  
  
## Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `NumberFormat`.  
  
|||  
|-|-|  
|Proprietà|Descrizione|  
|[Costruttore](../../javascript/reference/constructor-property-intl-numberformat.md)|Specifica la funzione tramite cui viene creato un oggetto formattatore di numeri.|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|Restituisce una funzione che formatta un numero utilizzando le impostazioni del formattatore del numero.|  
|[prototipo](../../javascript/reference/prototype-property-intl-numberformat.md)|Restituisce un riferimento al prototipo per un formattatore del numero.|  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `NumberFormat`:  
  
|||  
|-|-|  
|Metodo|Descrizione|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|Restituisce un oggetto in cui sono contenuti le proprietà e i valori dell'oggetto formattatore di numeri.|  
  
## Esempio  
 Nell'esempio seguente viene creato un oggetto `NumberFormat` per le impostazioni locali en\-US con le opzioni di formattazione specifiche.  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## Esempio  
 Negli esempi seguenti viene illustrato il risultato di utilizzare diverse impostazioni locali e opzioni.  
  
```javascript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [toLocaleString \(Number\)](../../javascript/reference/tolocalestring-number.md)   
 [Oggetto Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)   
 [Oggetto Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)