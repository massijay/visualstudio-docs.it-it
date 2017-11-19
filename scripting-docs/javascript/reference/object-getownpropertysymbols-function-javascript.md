---
title: Funzione Object. getownpropertysymbols (JavaScript) | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bcddba77305e30e4c5ae13f6b1fc5c9385b7108
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertysymbols-function-javascript"></a>Funzione Object.getOwnPropertySymbols (JavaScript)
Restituisce le proprietà di simboli propri di un oggetto. Le proprietà di simboli propri di un oggetto sono le proprietà definite direttamente sull'oggetto stesso e non ereditate dal prototipo dell'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### <a name="parameters"></a>Parametri  
 `object`  
 Obbligatorio. Oggetto che contiene i simboli propri.  
  
## <a name="return-value"></a>Valore restituito  
 Matrice che contiene i simboli propri dell'oggetto.  
  
## <a name="remarks"></a>Note  
 Per ottenere le proprietà dei simboli di un oggetto, sarà necessario usare `Object.getOwnPropertySymbols`. `Object.getOwnPropertyNames` non restituirà le proprietà dei simboli.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra come ottenere le proprietà dei simboli di un oggetto.  
  
```JavaScript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]