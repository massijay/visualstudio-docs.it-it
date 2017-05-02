---
title: "Metodo toFixed (Number) (JavaScript) | Microsoft Docs"
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
  - "toFixed"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Metodo toFixed"
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Metodo toFixed (Number) (JavaScript)
Rappresenta un numero con la notazione in virgola fissa.  
  
## Sintassi  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## Parametri  
 `numObj`  
 Un oggetto `Number` necessario.  
  
 `fractionDigits`  
 Opzionale.  Il numero di cifre dopo il separatore decimale.  Deve essere compreso tra 0 e 20 \(compresi\).  
  
## Valore restituito  
 Restituisce una rappresentazione in forma di stringa di un numero con la notazione in virgola fissa, contenente le cifre `fractionDigits` dopo il separatore decimale.  
  
 Se `fractionDigits` non viene fornito o è **undefined**, il valore predefinito è zero.  
  
## Esempio  
 Nel codice riportato di seguito viene illustrato come utilizzare `toFixed`.  
  
```javascript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto Number](../../javascript/reference/number-object-javascript.md)  
  
## Vedere anche  
 [Metodo toExponential \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [Metodo toPrecision \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)