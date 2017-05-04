---
title: "Metodo splice (Array) (JavaScript) | Microsoft Docs"
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
  - "splice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "splice (metodo)"
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Metodo splice (Array) (JavaScript)
Rimuove elementi da una matrice e, se necessario, li sostituisce con nuovi elementi restituendo gli elementi eliminati.  
  
## Sintassi  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## Parametri  
 `arrayObj`  
 Obbligatorio.  Oggetto `Array`.  
  
 `start`  
 Obbligatorio.  Posizione in base zero nella matrice da cui iniziare la rimozione degli elementi.  
  
 `deleteCount`  
 Obbligatorio.  Numero di elementi da rimuovere.  
  
 `item1, item2,. . ., itemN`  
 Facoltativo.  Elementi da inserire nella matrice in sostituzione di quelli eliminati.  
  
## Note  
 Il metodo `splice` modifica `arrayObj` rimuovendo il numero specificato di elementi dalla posizione `start` e inserendone di nuovi.  Gli elementi eliminati vengono restituiti come nuovo oggetto `Array`.  
  
## Esempio  
 Nel codice seguente viene illustrato come utilizzare il metodo `splice`.  
  
```javascript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Metodo slice \(Array\)](../../javascript/reference/slice-method-array-javascript.md)