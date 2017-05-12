---
title: "Metodo reverse (JavaScript) | Microsoft Docs"
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
  - "reverse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "matrici [Visual Studio], inversione di elementi"
  - "reverse (metodo)"
  - "trasposizione di elementi"
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo reverse (JavaScript)
Inverte gli elementi in un `Array`.  
  
## Sintassi  
  
```  
  
arrayObj.reverse()   
```  
  
## Parametri  
 `arrayObj`  
 Necessario.  Qualsiasi oggetto `Array`.  
  
## Valore restituito  
 Matrice invertita.  
  
## Note  
 Il riferimento `arrayObj` richiesto è un oggetto `Array`.  
  
 Il metodo `reverse` inverte sul posto gli elementi di un oggetto `Array`.  Durante l'esecuzione del metodo non viene creato un nuovo oggetto `Array`.  
  
 Se gli elementi della matrice non sono adiacenti, il metodo `reverse` crea degli elementi che vanno a riempire gli spazi vuoti nella matrice.  A ciascuno degli elementi creati viene assegnato il valore `undefined`.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `reverse`.  
  
```javascript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vedere anche  
 [Metodo concat \(Array\)](../../javascript/reference/concat-method-array-javascript.md)