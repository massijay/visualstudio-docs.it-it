---
title: "Funzione String.raw (JavaScript) | Microsoft Docs"
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
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione String.raw (JavaScript)
Restituisce il formato di stringa non elaborata di una stringa di modello.  
  
## Sintassi  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### Parametri  
 `templateStr`  
 Necessario.  Stringa di modello.  
  
 `obj`  
 Necessario.  Oggetto ben formato specificato usando la notazione del valore letterale dell'oggetto, ad esempio { raw: 'valore' }.  
  
 `...substitutions`  
 Parametro facoltativo.  Matrice \([parametro rest](../../javascript/functions-javascript.md)\) costituita da uno o più valori di sostituzione.  
  
## Note  
 La funzione `String.raw` deve essere usata con [stringhe di modello](../../javascript/advanced/template-strings-javascript.md).  La stringa non elaborata includerà qualsiasi carattere di escape e barra rovesciata presenti nella stringa.  
  
 Viene generato un errore se `obj` non è un oggetto ben formato.  
  
## Esempio  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]