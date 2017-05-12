---
title: "Oggetto Intl.Collator (JavaScript) | Microsoft Docs"
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
  - "Collator"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Oggetto Intl.Collator (JavaScript)
Fornisce confronti di stringhe specifici delle impostazioni locali.  
  
## Sintassi  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### Parametri  
 `collatorObj`  
 Necessario.  Il nome della variabile a cui assegnare l'oggetto `Collator`.  
  
 `locales`  
 Opzionale.  Una matrice di stringhe delle impostazioni locali che contengono uno o più linguaggi o tag per le impostazioni locali.  Se si include più di una stringa delle impostazioni locali, elencarle in ordine decrescente di priorità in modo che la prima voce siano le impostazioni locali desiderate.  Se si omette questo parametro, le impostazioni locali predefinite del runtime JavaScript vengono utilizzate.  Per ulteriori informazioni vedere la sezione Osservazioni.  
  
 `options`  
 Opzionale.  Oggetto che contiene una o più proprietà che specificano opzioni di confronto.  Per ulteriori informazioni, vedere la sezione relativa alle note.  
  
## Note  
 Il parametro `locales` deve rispettare il linguaggio [BCP 47](http://tools.ietf.org/html/rfc5646) o i tag per le impostazioni locali come "en\-US" e "zh\-Hans\-cn".  Il tag può includere il linguaggio, l'area, il paese e il variant.  Per un elenco delle lingue, vedere la pagina relativa al [registro dei sottotag delle lingue IANA](http://go.microsoft.com/fwlink/p/?linkid=227303).  Per esempi di tag di lingua, vedere l'[Appendice A](http://tools.ietf.org/html/rfc5646#appendix-A) di BCP 47.  Per `Collator`, è possibile includere l'estensione \-u nella stringa delle impostazioni locali per specificare almeno una delle estensioni Unicode seguenti:  
  
-   \- co per specificare le regole di confronto variant \(specifiche delle impostazioni locali\): "*language*\-*region*\- u\-co\-*value*".  
  
-   \-kn per specificare un confronto numerico: "*language*\-*region*\-u\-kn\-true&#124;false".  
  
-   –kf per specificare se ordinare innanzitutto i caratteri maiuscoli o minuscoli: "*language*\-*region*\-u\-kf\-upper&#124;lower&#124;false"\).  Questa estensione non è attualmente supportata.  
  
 Per specificare un confronto numerico, è possibile impostare: l'estensione del kn nella stringa delle impostazioni locali oppure utilizzare la proprietà `numeric` nel parametro `options`.  Se si utilizza la proprietà `numeric`, il valore –kn non verrà applicato.  
  
 Il parametro `options` può includere le seguenti proprietà:  
  
-   `localeMatcher`.  Specifica l'algoritmo di corrispondenza delle impostazioni locali da utilizzare.  I valori possibili sono "lookup" e "best fit".  Il valore predefinito è "più appropriato".  
  
-   `usage`.  Specifica se l'obiettivo di confronto viene ordinato o cercato.  I valori possibili sono "sort" e "search".  Il valore predefinito è "ordinamento".  
  
-   `sensitivity`.  Specifica la sensibilità dell'utilità di confronto.  I valori possibili sono "base", "accent", "case" e "variant".  Il valore predefinito è `undefined`.  
  
-   `ignorePunctuation`.  Specifica se la punteggiatura viene ignorata nel confronto.  I valori possibili sono "true" e "false".  Il valore predefinito è `false`.  
  
-   `numeric`.  Specifica se l'ordinamento numerico viene utilizzato.  I valori possibili sono "true" e "false".  Il valore predefinito è `false`.  
  
-   `caseFirst`.  Attualmente non supportato.  
  
## Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `Collator`.  
  
|||  
|-|-|  
|Proprietà|Descrizione|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|Restituisce una funzione che confronta due stringhe utilizzando l'ordinamento dell'utilità di confronto.|  
|[Costruttore](../../javascript/reference/constructor-property-intl-collator.md)|Specifica la funzione che crea un'utilità di confronto|  
|[prototipo](../../javascript/reference/prototype-property-intl-collator.md)|Restituisce un riferimento al prototipo per un'utilità di confronto.|  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `Collator`:  
  
|||  
|-|-|  
|Metodo|Descrizione|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Restituisce un oggetto che contiene le proprietà e i valori dell'utilità di confronto.|  
  
## Esempio  
 Nell'esempio seguente viene creato un oggetto `Collator` e viene eseguito un confronto.  
  
```javascript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## Esempio  
 Il seguente esempio utilizza oggetti `Collator` per ordinare una matrice.  Questo esempio mostra le differenze specifiche delle impostazioni locali.  
  
```javascript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## Esempio  
 Nell'esempio seguente viene utilizzato un oggetto `Collator` per trovare una stringa e specificare le opzioni di confronto.  
  
```javascript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [Metodo localeCompare \(String\)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Oggetto Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Oggetto Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)