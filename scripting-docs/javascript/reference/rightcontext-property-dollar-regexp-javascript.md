---
title: "Propriet&#224; rightContext ($&#39;) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$'"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "rightContext (proprietà) ($')"
ms.assetid: 6999c056-d18c-4583-9dd9-8fbb6d3d0ee7
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Propriet&#224; rightContext ($&#39;) (RegExp) (JavaScript)
Restituisce i caratteri a partire dalla posizione successiva all'ultima corrispondenza fino alla fine della stringa in cui è stata eseguita la ricerca.  Sola lettura.  
  
## Sintassi  
  
```  
  
RegExp.rightContext  
```  
  
## Note  
 L'oggetto associato a questa proprietà è sempre l'oggetto `RegExp` globale.  
  
 Il valore iniziale della proprietà **rightContext** è rappresentato da una stringa vuota.  Il valore della proprietà **rightContext** cambia ogni volta che viene individuata una corrispondenza corretta.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà **rightContext**:  
  
```javascript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## Vedere anche  
 [Proprietà $1...$9 \(RegExp\)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [Proprietà index \(RegExp\)](../../javascript/reference/index-property-regexp-javascript.md)   
 [Proprietà input \($\_\) \(RegExp\)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [Proprietà lastIndex \(RegExp\)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [Proprietà lastMatch \($&\) \(RegExp\)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [Proprietà lastParen \($\+\) \(RegExp\)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [Proprietà leftContext \($\`\) \(RegExp\)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)