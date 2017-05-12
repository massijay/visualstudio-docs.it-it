---
title: "Metodo slice (Array) (JavaScript) | Microsoft Docs"
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
  - "Indice a base zero"
  - "Array (oggetto)"
  - "slice (metodo)"
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Metodo slice (Array) (JavaScript)
Restituisce una sezione di una matrice.  
  
## Sintassi  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## Parametri  
 `arrayObj`  
 Obbligatorio.  Oggetto `Array`.  
  
 `start`  
 Obbligatorio.  Inizio della parte specificata di `arrayObj`.  
  
 `end`  
 Facoltativo.  Fine della parte specificata di `arrayObj`.  
  
## Note  
 Il metodo `slice` restituisce un oggetto `Array` contenente la parte specificata di `arrayObj`.  
  
 Il metodo `slice` esegue la copia fino all'elemento indicato da `end` escluso.  Se `start` è negativo, viene considerato come `length` \+ `start`, dove `length` rappresenta la lunghezza della matrice.  Se `end` è negativo, viene considerato come `length` \+ `end`, dove `length` rappresenta la lunghezza della matrice.  Se `end` viene omesso, l'estrazione prosegue fino alla fine di `arrayObj`.  Se `end` si trova prima di `start`, nessun elemento viene copiato nella nuova matrice.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `slice`.  Nel primo esempio tutti gli elementi di `myArray` tranne l'ultimo vengono copiati in `newArray`.  Nel secondo esempio solo gli ultimi due elementi di `myArray` vengono copiati in `newArray`.  
  
```javascript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vedere anche  
 [Metodo slice \(String\)](../../javascript/reference/slice-method-string-javascript.md)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)