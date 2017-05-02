---
title: "Metodo toPrecision (Number) (JavaScript) | Microsoft Docs"
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
  - "toPrecision"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Metodo toPrecision"
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Metodo toPrecision (Number) (JavaScript)
Rappresenta un numero in notazione esponenziale o a virgola fissa con un numero specificato di cifre.  
  
## Sintassi  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## Parametri  
 `numObj`  
 Obbligatorio.  Oggetto `Number`.  
  
 `precision`  
 Facoltativo.  Numero di cifre significative.  Deve essere compreso tra 1 e 21 \(inclusi\).  
  
## Valore restituito  
 Per i numeri in notazione esponenziale, dopo il separatore decimale vengono restituite le cifre `precision` \- 1.  Per i numeri a notazione fissa, vengono restituite le cifre significative `precision`.  
  
 Se `precision` non viene fornito o è **undefined**, viene chiamato il metodo **toString**.  
  
## Esempio  
 Nel codice seguente viene illustrato come utilizzare `toPrecision`.  
  
```javascript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto Number](../../javascript/reference/number-object-javascript.md)  
  
## Vedere anche  
 [Metodo toFixed \(Number\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [Metodo toExponential \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)