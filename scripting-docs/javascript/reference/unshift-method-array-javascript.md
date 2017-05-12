---
title: "Metodo unshift (Array) (JavaScript) | Microsoft Docs"
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
  - "unshift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "unshift (metodo)"
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Metodo unshift (Array) (JavaScript)
Inserisce nuovi elementi all'inizio di una matrice.  
  
## Sintassi  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## Parametri  
 `arrayObj`  
 Obbligatorio.  Oggetto `Array`.  
  
 `item1, item2,. . ., itemN`  
 Facoltativo.  Elementi da inserire all'inizio di `Array`.  
  
## Note  
 Il metodo `unshift` consente di inserire elementi all'inizio di una matrice in modo che appaiano nello stesso ordine in cui sono riportati nell'elenco degli argomenti.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `unshift`.  
  
```javascript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Metodo shift \(Array\)](../../javascript/reference/shift-method-array-javascript.md)