---
title: "Oggetto Number (JavaScript) | Microsoft Docs"
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
  - "Number_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Number (oggetto)"
ms.assetid: 76e87c37-cf6c-46cc-bafa-04be1fe3d78d
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Oggetto Number (JavaScript)
Oggetto che rappresenta un numero di qualsiasi tipo.  Tutti i numeri JavaScript sono numeri a virgola mobile a 64 bit.  
  
## Sintassi  
  
```  
  
numObj = new Number(value)  
```  
  
## Parametri  
 `numObj`  
 Obbligatorio.  Nome della variabile a cui l'oggetto `Number` è assegnato.  
  
 `value`  
 Obbligatorio.  Il valore numerico.  
  
## Note  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] crea oggetti `Number` quando una variabile viene impostata su un valore numerico, ad esempio `var num = 255.336;`.  Raramente è necessario creare oggetti `Number` in modo esplicito.  
  
 L'oggetto `Number` dispone di proprietà e metodi personalizzati, oltre alle proprietà e ai metodi ereditati da `Object`.  In alcuni casi i numeri vengono convertiti in stringhe, ad esempio quando un numero viene aggiunto o concatenato a una stringa, oltre che per mezzo del metodo `toString`.  Per altre informazioni, vedere [Operatore addizione \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md).  
  
 JavaScript ha diverse costanti numeriche.  Per un elenco completo, vedere [Costanti Number](../../javascript/reference/number-constants-javascript.md).  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Proprietà  
 La tabella seguente elenca le proprietà dell'oggetto `Number` .  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà constructor](../../javascript/reference/constructor-property-object-javascript.md)|Specifica la funzione che crea un oggetto.|  
|[Proprietà prototype](../../javascript/reference/prototype-property-object-javascript.md)|Restituisce un riferimento al prototipo per una classe di oggetti.|  
  
## Funzioni  
 La tabella seguente elenca le funzioni dell'oggetto `Number` .  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[Funzione Number.isFinite](../../javascript/reference/number-isfinite-function-number-javascript.md)|Restituisce un valore booleano che indica se un valore è finito.|  
|[Funzione Number.isInteger](../../javascript/reference/number-isinteger-function-number-javascript.md)|Restituisce un valore booleano che indica se un valore è un numero intero.|  
|[Funzione Number.isNaN](../../javascript/reference/number-isnan-function-number-javascript.md)|Restituisce un valore booleano che indica se un valore è il valore riservato `NaN` \(non un numero\).|  
|[Number.isSafeInteger](../../javascript/reference/number-issafeinteger-number-javascript.md)|Restituisce un valore booleano che indica se un valore può essere rappresentato senza problemi in JavaScript.|  
  
## Metodi  
 La tabella seguente elenca i metodi dell'oggetto `Number` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Restituisce un valore booleano che indica se per un oggetto è disponibile una proprietà con il nome specificato.|  
|[Metodo isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Restituisce un valore booleano che indica se un oggetto esiste nella gerarchia di prototipi di un altro oggetto.|  
|[Metodo propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Restituisce un valore booleano che indica se una proprietà specificata è parte di un oggetto e se è enumerabile.|  
|[Metodo toExponential](../../javascript/reference/toexponential-method-number-javascript.md)|Restituisce una stringa che contiene un numero rappresentato nella notazione esponenziale.|  
|[Metodo toFixed](../../javascript/reference/tofixed-method-number-javascript.md)|Restituisce una stringa che rappresenta un numero nella notazione a virgola fissa.|  
|[Metodo toLocaleString](../../javascript/reference/tolocalestring-number.md)|Restituisce un oggetto convertito in una stringa in base alle impostazioni locali correnti.|  
|[Metodo toPrecision](../../javascript/reference/toprecision-method-number-javascript.md)|Restituisce una stringa che contiene un numero rappresentato nella notazione esponenziale o a virgola fissa e formato da un numero specificato di cifre.|  
|[Metodo toString](../../javascript/reference/tostring-method-object-javascript.md)|Restituisce la rappresentazione in formato stringa di un oggetto.|  
|[Metodo valueOf](../../javascript/reference/valueof-method-object-javascript.md)|Restituisce il valore primitivo dell'opzione specificata.|  
  
## Vedere anche  
 [Oggetti JavaScript](../../javascript/reference/javascript-objects.md)   
 [Oggetto Math](../../javascript/reference/math-object-javascript.md)   
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)