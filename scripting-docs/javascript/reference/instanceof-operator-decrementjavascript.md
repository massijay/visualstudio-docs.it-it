---
title: Operatore instanceof (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: instanceof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: instanceOf operator
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 672047cb066a812d16edc693638c3d6d8295798b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="instanceof-operator-javascript"></a>Operatore instanceof (JavaScript)
Restituisce un valore booleano che indica se un oggetto è o meno un'istanza di una classe particolare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
result = object instanceof class  
```  
  
## <a name="parameters"></a>Parametri  
 `result`  
 Obbligatorio. Qualsiasi variabile.  
  
 `object`  
 Obbligatorio. Qualsiasi espressione oggetto.  
  
 `class`  
 Obbligatorio. Qualsiasi classe di oggetto definita.  
  
## <a name="remarks"></a>Note  
 L'operatore `instanceof` restituisce `true` se `object` rappresenta un'istanza di `class`. Restituisce `true` se `true` se è presente `class` nella catena di prototipi dell'oggetto. Restituisce `false` se `object` non è un'istanza di `class` o se `object` è `null`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare l'operatore `instanceof`.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza tra operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)