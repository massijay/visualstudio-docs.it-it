---
title: "Propriet&#224; $1...$9 (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$1...$9"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "$1...$9 (proprietà)"
ms.assetid: 8bd84851-f62f-4eb1-a93d-b67135ea091a
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Propriet&#224; $1...$9 (RegExp) (JavaScript)
Restituisce le nove parti memorizzate più di recente individuate durante l'applicazione di un criterio di ricerca.  Sola lettura.  
  
## Sintassi  
  
```  
  
RegExp.$n   
```  
  
## Parametri  
 `RegExp`  
 Sempre l'oggetto globale `RegExp`.  
  
 `n`  
 Qualsiasi numero intero compreso tra 1 e 9.  
  
## Note  
 I valori delle proprietà **$1...$9** vengono modificati ogni volta che viene individuata una corrispondenza corretta tra parentesi.  In un criterio di ricerca di espressioni regolari è possibile specificare qualsiasi numero di sottostringhe tra parentesi, ma soltanto le ultime nove vengono archiviate.  
  
## Esempio  
 Nell'esempio seguente viene eseguita una ricerca di espressioni regolari.  Visualizza le corrispondenze e le sottocorrispondenze dell'oggetto `RegExp` globale.  Le sottocorrispondenze rappresentano le corrispondenze corrette tra parentesi contenute nelle proprietà `$1…$9`.  Nell'esempio vengono inoltre visualizzate le corrispondenze e le sottocorrispondenze della matrice restituita dal metodo `exec`.  
  
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
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## Vedere anche  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)