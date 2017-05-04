---
title: "Operatore instanceof (JavaScript) | Microsoft Docs"
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
  - "instanceof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "instanceOf (operatore)"
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Operatore instanceof (JavaScript)
Restituisce un valore booleano che indica se un oggetto è o meno un'istanza di una classe particolare.  
  
## Sintassi  
  
```  
  
result = object instanceof class  
```  
  
## Parametri  
 `result`  
 Necessario.  Qualsiasi variabile.  
  
 `object`  
 Necessario.  Qualsiasi espressione oggetto.  
  
 `class`  
 Necessario.  Qualsiasi classe di oggetto definita.  
  
## Note  
 L'operatore `instanceof` restituisce `true` se `object` rappresenta un'istanza di `class`.  Restituisce `true` se `true` se è presente `class` nella catena di prototipi dell'oggetto.  Restituisce `false` se `object` non è un'istanza di `class` o se `object` è `null`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare l'operatore `instanceof`.  
  
```javascript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Vedere anche  
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)