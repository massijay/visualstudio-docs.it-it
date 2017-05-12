---
title: "Metodo lastIndexOf (String) (JavaScript) | Microsoft Docs"
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
  - "lastIndexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndexOf (metodo), string"
  - "stringa, metodo lastIndexOf"
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Metodo lastIndexOf (String) (JavaScript)
Restituisce l'ultima occorrenza di una sottostringa nella stringa.  
  
## Sintassi  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## Parametri  
 `strObj`  
 Obbligatorio.  Oggetto `String` o valore letterale stringa.  
  
 `substring`  
 Obbligatorio.  Sottostringa da cercare.  
  
 `startindex`  
 Facoltativo.  Indice da cui iniziare la ricerca.  Se omesso, la ricerca inizierà dalla fine della stringa.  
  
## Note  
 Il metodo **lastIndexOf** restituisce un valore intero che indica l'inizio della sottostringa nell'oggetto `String`.  Se la sottostringa non viene trovata, viene restituito \-1.  
  
 Se `startindex` è negativo, `startindex` viene considerato uguale a zero.  Se è maggiore dell'indice corrispondente alla posizione del carattere più grande, viene considerato come indice massimo.  
  
 La ricerca viene eseguita partendo dall'ultimo carattere della stringa.  Per tutti gli altri aspetti, questo metodo è identico a **indexOf**.  
  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo **lastIndexOf**.  
  
```javascript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo indexOf \(String\)](../../javascript/reference/indexof-method-string-javascript.md)