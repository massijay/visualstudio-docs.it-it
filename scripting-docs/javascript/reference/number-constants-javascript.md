---
title: "Costanti Number (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "costanti [JavaScript], numero"
  - "MAX_VALUE (costante) [JavaScript]"
  - "MIN_VALUE (costante) [JavaScript]"
  - "NaN (costante) [JavaScript]"
  - "NEGATIVE_INFINITY (costante) [JavaScript]"
  - "number (costanti) [JavaScript]"
  - "Number.MAX_VALUE (costante) [JavaScript]"
  - "Number.MIN_VALUE (costante) [JavaScript]"
  - "Number.NaN (costante) [JavaScript]"
  - "Number.NEGATIVE_INFINITY (costante) [JavaScript]"
  - "Number.POSITIVE_INFINITY (costante) [JavaScript]"
  - "POSITIVE_INFINITY (costante) [JavaScript]"
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Costanti Number (JavaScript)
Le seguenti costanti numeriche sono proprietà dell'oggetto `Number`.  
  
## Costanti numeriche oggetto  
 Per accedere a queste costanti non è necessario creare l'oggetto `Number`.  
  
|Costante|Valore restituito|  
|--------------|-----------------------|  
|`Number.EPSILON`|Il numero più basso che può essere rappresentato in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Equivale approssimativamente a 2.2204460492503130808472633361816E\-16.|  
|`Number.MAX_SAFE_INTEGER`|Il numero più alto che può essere rappresentato in modo sicuro in JavaScript.  È pari a 9007199254740991.|  
|`Number.MAX_VALUE`|Il numero più alto che può essere rappresentato in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Equivale approssimativamente a 1.79E\+308.|  
|`Number.MIN_SAFE_INTEGER`|Il numero più piccolo che può essere rappresentato in modo sicuro in JavaScript.  È pari a \-9007199254740991.|  
|`Number.MIN_VALUE`|Il numero più vicino allo zero che può essere rappresentato in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Equivale approssimativamente a 5.00E\-324.|  
|`Number.NaN`|Un valore che non sia un numero.<br /><br /> Nei confronti di uguaglianza, `NaN` non equivale a nessun valore, incluso se stesso.  Per verificare se il valore è equivalente a `NaN`, usare la [funzione isNaN](../../javascript/reference/isnan-function-javascript.md).|  
|`Number.NEGATIVE_INFINITY`|Un valore inferiore al numero negativo più alto che può essere rappresentato in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mostra valori `NEGATIVE_INFINITY` come `-infinity`.|  
|`Number.POSITIVE_INFINITY`|Un valore più alto del numero più alto che può essere rappresentato in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mostra valori `POSITIVE_INFINITY` come `infinity`.|  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Per `Number.EPSILON`, `Number.MAX_SAFE_INTEGER`, e `Number.MIN_SAFE_INTEGER`:  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Si applica a** : [Oggetto Number](../../javascript/reference/number-object-javascript.md)  
  
## Vedere anche  
 [Costanti Math](../../javascript/reference/math-constants-javascript.md)   
 [Costanti JavaScript](../../javascript/reference/javascript-constants.md)   
 [Costante Infinity](../../javascript/reference/infinity-constant-javascript.md)   
 [Costante NaN](../../javascript/reference/nan-constant-javascript.md)   
 [Funzione isNaN](../../javascript/reference/isnan-function-javascript.md)