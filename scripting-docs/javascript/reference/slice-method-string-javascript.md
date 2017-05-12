---
title: "Metodo slice (String) (JavaScript) | Microsoft Docs"
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
  - "slice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "slice (metodo)"
  - "stringhe [Visual Studio], restituzione di caratteri"
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Metodo slice (String) (JavaScript)
Restituisce una sezione di una stringa.  
  
## Sintassi  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## Parametri  
 `stringObj`  
 Necessario.  Un oggetto `String` o un valore letterale stringa.  
  
 `start`  
 Necessario.  Indice dell'inizio della parte specificata di `stringObj`.  
  
 `end`  
 Opzionale.  Indice della fine della parte specificata di `stringObj`.  La sottostringa include i caratteri fino al carattere indicato da `end` escluso.  Se questo valore viene omesso, verrà restituita la stringa compresa tra la posizione iniziale specificata e la fine di `stringObj`.  
  
## Note  
 Il metodo `slice` restituisce l'oggetto `String` che include la parte specificata di `stringObj`.  
  
 Il metodo `slice` esegue la copia fino al carattere indicato da `end` escluso.  
  
 Se `start` è negativo, verrà considerato come *length* \+ `start` dove *length* è la lunghezza della stringa.  Se `end` è negativo, verrà considerato come *length* \+ `end`.  Se `end` viene omesso, la copia continua fino alla fine di `stringObj`.  Se `end` si trova prima di `start`, nessun carattere verrà copiato nella nuova stringa.  
  
## Esempio  
 Nel primo esempio, il metodo `slice` restituisce l'intera stringa.  Nel secondo esempio, il metodo `slice` restituisce l'intera stringa, eccetto l'ultimo carattere.  
  
```javascript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo slice \(Array\)](../../javascript/reference/slice-method-array-javascript.md)