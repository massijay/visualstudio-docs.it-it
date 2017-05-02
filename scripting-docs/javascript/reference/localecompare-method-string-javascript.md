---
title: "Metodo localeCompare (String) (JavaScript) | Microsoft Docs"
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
  - "localeCompare"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "localeCompare (metodo)"
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Metodo localeCompare (String) (JavaScript)
Determina se due stringhe sono equivalenti nelle impostazioni locali correnti.  
  
## Sintassi  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## Parametri  
 `stringVar`  
 Necessario.  Prima stringa da confrontare.  
  
 `stringExp`  
 Necessario.  Seconda stringa da confrontare.  
  
 `locales`  
 Opzionale.  Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali.  Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate.  Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate.  Questo parametro deve essere conforme agli standard [BCP 47](http://tools.ietf.org/html/rfc5646); vedere l'[oggetto Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) per i dettagli.  
  
 `options`  
 Opzionale.  Oggetto che contiene una o più proprietà che specificano opzioni di confronto. Vedere [Oggetto Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) per i dettagli.  
  
## Note  
 Per le stringhe di confronto, è possibile specificare gli oggetti o i valori letterali stringa `String`.  
  
 A partire da Internet Explorer 11, in `localeCompare` viene utilizzato l'oggetto `Intl.Collator` internamente per l'esecuzione di confronti, tramite cui viene aggiunto il supporto per i parametri `options` e `locales`.  Per ulteriori informazioni su questi parametri, vedere [Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) e [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md).  
  
> [!IMPORTANT]
>  I parametri `options` e `locales` non sono supportati in tutte le modalità di documento e versioni del browser.  Per ulteriori informazioni, vedere la sezione Requisiti.  
  
 Il metodo `localeCompare` esegue un confronto basato sulle impostazioni locali tra `stringVar` e `stringExp` e restituisce uno dei seguenti valori, a seconda dell'ordinamento delle impostazioni locali predefinite del sistema.  
  
-   \-1 se `stringVar`, secondo l'ordinamento, precede `stringExp`.  
  
-   \+1 se `stringVar` si trova nell'ordine dopo `stringExp`.  
  
-   0 \(zero\) se le due stringhe sono equivalenti.  
  
## Esempio  
 Nel codice riportato di seguito viene illustrato come utilizzare `localeCompare`.  
  
```javascript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## Esempio  
 Nel codice seguente viene illustrato come utilizzare `localeCompare` con le impostazioni locali per la lingua tedesca \(Germania\).  
  
```javascript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## Esempio  
 Di seguito viene illustrato come utilizzare `localeCompare` con le impostazioni locali per la lingua tedesca \(Germania\) e un'estensione specifica delle impostazioni locali che specifica l'ordinamento per le guide telefoniche tedesche.  Questo esempio mostra le differenze specifiche delle impostazioni locali.  
  
```javascript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Parametri `locales` e `options`  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [Metodo toLocaleString \(Object\)](../../javascript/reference/tolocalestring-method-object-javascript.md)