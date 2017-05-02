---
title: "Funzione Math.abs (JavaScript) | Microsoft Docs"
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
  - "abs"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "valori assoluti, calcolo"
  - "valori assoluti"
  - "numeriche (espressioni)"
  - "abs (metodo)"
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Funzione Math.abs (JavaScript)
Restituisce il valore assoluto di un numero \(il valore senza considerare se è positivo o negativo\).  Ad esempio, il valore assoluto di \-5 corrisponde al valore assoluto di 5.  
  
## Sintassi  
  
```  
Math.abs(number)  
```  
  
#### Parametri  
 L'argomento obbligatorio `number` è un'espressione numerica per la quale si richiede il valore assoluto.  
  
## Valore restituito  
 Il valore assoluto dell'argomento `number`.  
  
## Esempio  
 Nel seguente esempio viene illustrato l'utilizzo della funzione `abs`:  
  
```javascript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Math](../../javascript/reference/math-object-javascript.md)  
  
## Vedere anche  
 [Oggetto Math](../../javascript/reference/math-object-javascript.md)