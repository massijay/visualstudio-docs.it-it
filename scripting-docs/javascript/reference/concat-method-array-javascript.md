---
title: "Metodo concat (Array) (JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat (metodo) (array)"
  - "Concat (metodo)"
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Metodo concat (Array) (JavaScript)
Combina due o più matrici.  
  
## Sintassi  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## Parametri  
 `array1`  
 Obbligatorio.  Oggetto `Array` a cui sono concatenate tutte le altre matrici.  
  
 `item1,. . ., itemN`  
 Facoltativo.  Elementi aggiuntivi da aggiungere alla fine di `array1`.  
  
## Note  
 Il metodo `concat` restituisce un oggetto `Array` che contiene la concatenazione di `array1` e degli altri elementi forniti.  
  
 Gli elementi da aggiungere \(*item1 itemN*\) alla matrice vengono aggiunti in ordine a partire dal primo elemento dell'elenco.  Se uno degli elementi è una matrice, il relativo contenuto viene aggiunto alla fine di `array1`.  Se non è una matrice, l'elemento viene aggiunto alla fine della matrice come singolo elemento.  
  
 Elementi di matrici di origine vengono copiati nella matrice risultante nel modo seguente:  
  
-   Se un oggetto viene copiato da una delle matrici da concatenare alla nuova matrice, il riferimento dell'oggetto continua a puntare allo stesso oggetto.  Una modifica apportata alla nuova matrice o alla matrice originale verrà apportata a entrambe le matrici.  
  
-   Se alla nuova matrice viene aggiunto un valore numerico o stringa, viene copiato solo il valore.  La modifica del valore in una matrice non influisce sul valore dell'altra.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare il metodo `concat` quando abbinato a una matrice:  
  
```javascript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vedere anche  
 [Metodo concat \(String\)](../../javascript/reference/concat-method-string-javascript.md)   
 [Metodo join \(Array\)](../../javascript/reference/join-method-array-javascript.md)