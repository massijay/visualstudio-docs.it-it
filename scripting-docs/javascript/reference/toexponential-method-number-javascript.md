---
title: "Metodo toExponential (Number) (JavaScript) | Microsoft Docs"
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
  - "toExponential"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Metodo toExponential"
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Metodo toExponential (Number) (JavaScript)
Rappresenta un numero in notazione esponenziale.  
  
## Sintassi  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## Parametri  
 `numObj`  
 Obbligatorio.  Oggetto **Number**.  
  
 `fractionDigits`  
 Facoltativo.  Numero di cifre dopo il separatore decimale.  Deve essere compreso tra 0 e 20 \(inclusi\).  
  
## Valore restituito  
 Restituisce una rappresentazione in forma di stringa di un numero in notazione esponenziale.  La stringa contiene una cifra prima del separatore decimale e può contenere cifre `fractionDigits` dopo di essa.  
  
 Se `fractionDigits` non viene fornito, il metodo `toExponential` restituisce il numero di cifre necessarie per specificare il numero in modo univoco.  
  
## Esempio  
  
```javascript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto Number](../../javascript/reference/number-object-javascript.md)  
  
## Vedere anche  
 [Metodo toFixed \(Number\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [Metodo toPrecision \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)