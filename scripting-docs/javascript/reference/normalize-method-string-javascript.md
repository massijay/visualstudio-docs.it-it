---
title: "Metodo normalize (stringa) (JavaScript) | Microsoft Docs"
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
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo normalize (stringa) (JavaScript)
Restituisce il formato di normalizzazione Unicode di una stringa specificata.  
  
## Sintassi  
  
```  
stringObj.normalize([form]);  
```  
  
#### Parametri  
 `stringObj`  
 Necessario.  Oggetto stringa rispetto da testare.  
  
 `form`  
 Parametro facoltativo.  Valore del formato di normalizzazione Unicode.  
  
## Valore restituito  
 Formato di normalizzazione Unicode di una stringa specificata.  
  
## Eccezioni  
 Se `form` è un valore non supportato, viene generato un oggetto `RangeError`.  
  
## Note  
 Se `stringObj` non è una stringa, viene convertito in stringa prima che il metodo tenti di restituire il formato di normalizzazione Unicode della stringa.  
  
 `form` deve essere il valore del formato di normalizzazione Unicode, "NFC", "NFD", "NFKC" o "NFKD", corrispondente ai valori specificati per [Unicode Standard Annex \#15](http://www.unicode.org/reports/tr15/).  Il valore predefinito di `form` è "NFC".  
  
## Esempio  
 Negli esempi di codice viene mostrato utilizzare questo `normalize` metodo.  
  
```javascript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]