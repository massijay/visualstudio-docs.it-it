---
title: "Metodo substr (String) (JavaScript) | Microsoft Docs"
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
  - "substr"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "substr (metodo)"
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodo substr (String) (JavaScript)
Ottiene una sottostringa di lunghezza specifica che inizia dalla posizione specificata.  
  
## Sintassi  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## Parametri  
 `stringvar`  
 Obbligatorio.  Un valore letterale stringa o un oggetto `String` da cui viene estratta la sottostringa.  
  
 `start`  
 Obbligatorio.  Posizione iniziale della sottostringa desiderata.  L'indice del primo carattere della stringa è zero.  
  
 `length`  
 Facoltativo.  Numero di caratteri da includere nella sottostringa restituita.  
  
## Note  
 Se l'argomento `length` è zero o un numero negativo, verrà restituita una stringa vuota.  Se omesso, verrà restituita la stringa compresa tra la posizione iniziale specificata e la fine di `stringvar`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `substr`.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo substring \(String\)](../../javascript/reference/substring-method-string-javascript.md)