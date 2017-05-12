---
title: "Propriet&#224; compare (Intl.Collator) | Microsoft Docs"
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
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Propriet&#224; compare (Intl.Collator)
Restituisce una funzione che confronta due stringhe utilizzando l'ordinamento dell'utilità di confronto.  
  
## Sintassi  
  
```javascript  
collatorObj.compare  
```  
  
#### Parametri  
 `collatorObj`  
 Necessario.  Il nome dell'oggetto `Collator` da utilizzare per il confronto.  
  
## Note  
 La funzione restituita dalla proprietà `compare` accetta due argomenti, `x` e `y` e restituisce il risultato di un confronto delle impostazioni locali specifico di `x` e `y` utilizzando le opzioni specificate nell'oggetto `Collator`.  
  
 Il risultato del confronto sarà:  
  
-   \-1 se `x`, secondo l'ordinamento, precede `y`.  
  
-   0 \(zero\) se `x` è uguale a `y` nell'ordinamento.  
  
-   1 se `x`, secondo l'ordinamento, è dopo `y`.  
  
## Esempio  
 Nell'esempio seguente viene creato un oggetto `Collator` e viene eseguito un confronto.  
  
```javascript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
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
 Nell'esempio seguente si utilizza un oggetto `Collator` per cercare una stringa.  
  
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
 [Oggetto Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)