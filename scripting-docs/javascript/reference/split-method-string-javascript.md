---
title: "Metodo split (String) (JavaScript) | Microsoft Docs"
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
  - "split"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "split (metodo)"
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Metodo split (String) (JavaScript)
Suddivide una stringa in sottostringhe utilizzando il separatore specificato e le restituisce come matrice.  
  
## Sintassi  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## Parametri  
 `stringObj`  
 Obbligatorio.  Oggetto `String` o valore letterale stringa da suddividere.  L'oggetto non viene modificato con il metodo **split**.  
  
 `separator`  
 Facoltativa.  Stringa o oggetto **Regular Expression** che identifica uno o più caratteri da utilizzare nella separazione della stringa.  Se omesso, verrà restituita una matrice a elemento singolo contenente l'intera stringa.  
  
 `limit`  
 Facoltativa.  Valore utilizzato per limitare il numero di elementi restituiti nella matrice.  
  
## Valore restituito  
 Il risultato del metodo **split** è una matrice di stringhe suddivise in ciascun punto in cui si trova `separator` in `stringObj`.  `separator` non verrà restituito come parte di alcun elemento della matrice.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo **split**.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo concat \(String\)](../../javascript/reference/concat-method-string-javascript.md)   
 [Oggetto RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Applicazione di esempio per scorrimento, panoramica e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)