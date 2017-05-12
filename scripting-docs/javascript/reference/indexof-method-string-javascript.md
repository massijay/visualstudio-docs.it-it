---
title: "Metodo indexOf (String) (JavaScript) | Microsoft Docs"
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
  - "indexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "indexOf (metodo), stringa"
  - "stringa, indexOf (metodo)"
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Metodo indexOf (String) (JavaScript)
Restituisce la posizione della prima occorrenza di una sottostringa.  
  
## Sintassi  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## Parametri  
 `strObj`  
 Obbligatorio.  Oggetto `String` o valore letterale stringa.  
  
 `subString`  
 Obbligatorio.  Sottostringa da cercare nella stringa  
  
 `startIndex`  
 Facoltativa.  Indice dal quale iniziare la ricerca dell'oggetto `String`.  Se omesso, la ricerca verrà eseguita a partire dall'inizio della stringa.  
  
## Note  
 Il metodo **indexOf** restituisce l'inizio della sottostringa nell'oggetto `String`.  Se la ricerca ha esito negativo, verrà restituito \-1.  
  
 Se `startindex` è negativo, `startindex` viene considerato pari a zero.  Se è maggiore dell'indice più alto, viene considerato come l'indice più alto.  
  
 La ricerca viene eseguita da sinistra a destra.  Per tutti gli altri aspetti, questo metodo è identico a **lastIndexOf**.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo **indexOf**.  
  
```javascript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo lastIndexOf \(String\)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [Applicazione di esempio per scorrimento, panoramica e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)