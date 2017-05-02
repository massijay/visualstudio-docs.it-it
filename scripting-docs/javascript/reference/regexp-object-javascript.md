---
title: "Oggetto RegExp (JavaScript) | Microsoft Docs"
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
  - "RegExp"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp (oggetto)"
  - "RegExp (oggetto), panoramica"
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Oggetto RegExp (JavaScript)
Oggetto globale intrinseco che archivia informazioni sui risultati delle corrispondenze di criteri di ricerca di espressioni regolari.  
  
## Sintassi  
  
```  
  
RegExp.property   
```  
  
## Note  
 L'argomento *property* obbligatorio può essere una delle proprietà dell'oggetto `RegExp`.  
  
 L'oggetto `RegExp` non può essere creato in modo diretto, ma è sempre disponibile per l'utilizzo.  I valori riportati nella tabella che segue corrispondono ai valori iniziali delle diverse proprietà dell'oggetto `RegExp`, fino a quando non viene completata correttamente una ricerca di espressioni regolari:  
  
|Proprietà|Abbreviazione|Valore iniziale|  
|---------------|-------------------|---------------------|  
|index||\-1|  
|input|$\_|Stringa vuota.|  
|lastIndex||\-1|  
|lastMatch|$&|Stringa vuota.|  
|lastParen|$\+|Stringa vuota.|  
|leftContext|$\`|Stringa vuota.|  
|rightContext|$'|Stringa vuota.|  
|$1 \- $9|$1 \- $9|Stringa vuota.|  
  
 Il valore delle proprietà corrisponde a non definito fino a quando non viene completata correttamente una ricerca di espressioni regolari.  
  
 L'oggetto `RegExp` globale non deve essere confuso con l'oggetto **Regular Expression**.  Anche se sembrano uguali, sono distinti e separati.  Le proprietà dell'oggetto `RegExp` globale contengono informazioni continuamente aggiornate su ciascuna corrispondenza non appena questa si verifica, mentre le proprietà dell'oggetto **Regular Expression** contengono solo informazioni sulle corrispondenze che si verificano con tale istanza di **Regular Expression**.  
  
## Esempio  
 Nell'esempio seguente viene eseguita una ricerca di espressioni regolari.  Vengono visualizzate corrispondenze e sottocorrispondenze dell'oggetto `RegExp` globale e della matrice restituita dal metodo `exec`.  
  
```javascript  
var newLine = "<br />";  
  
var re = /(\w+)@(\w+)\.(\w+)/g  
var src = "Please send mail to george@contoso.com and someone@example.com. Thanks!"  
  
var result;  
var s = "";  
  
// Get the first match.  
result = re.exec(src);  
  
while (result != null) {  
    // Show the entire match.  
    s += newLine;  
  
    // Show the match and submatches from the RegExp global object.  
    s += "RegExp.lastMatch: " + RegExp.lastMatch + newLine;  
    s += "RegExp.$1: " + RegExp.$1 + newLine;  
    s += "RegExp.$2: " + RegExp.$2 + newLine;  
    s += "RegExp.$3: " + RegExp.$3 + newLine;  
  
    // Show the match and submatches from the array that is returned  
    // by the exec method.  
    for (var index = 0; index < result.length; index++) {  
        s +=  index + ": ";  
        s += result[index];  
        s += newLine;  
    }  
  
    // Get the next match.  
    result = re.exec(src);  
}  
document.write(s);  
  
// Output:  
//  RegExp.lastMatch: george@contoso.com  
//  RegExp.$1: george  
//  RegExp.$2: contoso  
//  RegExp.$3: com  
//  0: george@contoso.com  
//  1: george  
//  2: contoso  
//  3: com  
  
//  RegExp.lastMatch: someone@example.com  
//  RegExp.$1: someone  
//  RegExp.$2: example  
//  RegExp.$3: com  
//  0: someone@example.com  
//  1: someone  
//  2: example  
//  3: com  
  
```  
  
<a name="js56jsobjregexpprop"></a>   
## Proprietà  
 [Proprietà $1...$9](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [Proprietà index](../../javascript/reference/index-property-regexp-javascript.md) &#124; [Proprietà input](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [Proprietà lastIndex](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [Proprietà lastMatch](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [Proprietà lastParen](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [Proprietà leftContext](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [Proprietà rightContext](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## Metodi  
 L'oggetto `RegExp` non contiene alcun metodo.  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vedere anche  
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)