---
title: "Stringhe di modello (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Stringhe di modello (JavaScript)
In [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] è possibile usare stringhe di modello per costruire valori letterali stringa con espressioni incorporate.  Le stringhe di modello forniscono anche supporto integrato per stringhe a più righe.  
  
 Per costruire una stringa di modello, usare l'accento grave, chiamato anche apice inverso \(\`\), per racchiudere la stringa, anziché le virgolette singole o doppie.  L'esempio di codice seguente mostra una stringa di modello semplice.  
  
```  
`Template strings can include 'single quotes' and "double quotes" inline.`  
  
```  
  
 Le stringhe di modello possono includere interruzioni di riga senza che sia necessario l'uso del carattere di avanzamento riga \(\\n\).  
  
```  
`Template strings can include line breaks and don't need the linefeed character.`  
```  
  
 Il carattere $ viene usato per specificare segnaposto all'interno di una stringa di modello.  La sintassi è ${*espressione*}, dove *espressione* è qualsiasi espressione JavaScript, ad esempio una variabile o una funzione, come mostrato nell'esempio seguente.  
  
```  
var name = "Bob";  
var str = `Hello ${name}, how are you this fine ${partOfDay()}?`  
console.log(str);  
  
function partOfDay () {  
    var hour = new Date().getHours();  
  
    if (hours <= 12) {  
        return “morning”;  
    } else if (hours <= 5) {  
        return “afternoon”;  
    } else {  
        return “evening”;  
    }  
}  
  
// Output:  
// Hello Bob, how are you this fine afternoon?  
```  
  
 Funzioni di modello con tag, che permettono di modificare il valore di una stringa di modello usando una funzione richiamata con argomenti dalla stringa di modello.  Il primo argomento è una matrice di valori letterali stringa, delimitata dalle espressioni della stringa di modello che contiene, mentre il secondo argomento è una matrice \([parametro Rest](../../javascript/functions-javascript.md)\) che contiene i valori delle espressioni della stringa di modello.  
  
 Nell'esempio seguente viene usata la funzione di modello con tag buildURL per costruire un URL.  La sintassi consiste nell'usare il nome della funzione seguito immediatamente dalla stringa di modello.  
  
```  
function buildURL(strArray, ...valArray) {  
    var newUrl = strArray[0] + "ja-ja" + "/" + valArray[1] +  
    "/" + valArray[2];  
  
    return newUrl;  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
console.log(url);  
  
// Output:  
// http://msdn.microsoft.com/ja-ja/library/dn771551.aspx  
```  
  
 Se è necessario accedere ai valori stringa non elaborata passati, il primo argomento passato alla funzione di modello con tag supporta una proprietà `raw` che restituisce il formato stringa non elaborata delle stringhe passate.  
  
```  
function buildURL(strArray, ...valArray) {  
    console.log(strArray.raw);  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
// Ouput:  
// http://msdn.microsoft.com/  
// /  
// en-us  
// library  
```  
  
> [!NOTE]
>  È anche possibile usare la funzione [String.raw](../../javascript/reference/string-raw-function-javascript.md) per restituire il formato stringa non elaborata di una stringa di modello.  
  
## Vedere anche  
 [Riferimento al linguaggio JavaScript](../../javascript/javascript-language-reference.md)   
 [JavaScript avanzato](../../javascript/advanced/advanced-javascript.md)