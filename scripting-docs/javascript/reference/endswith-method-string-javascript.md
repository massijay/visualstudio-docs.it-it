---
title: Metodo StartsWith (String) (JavaScript) | Documenti Microsoft
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
ms.assetid: c7d836e3-bc43-4d1b-be60-0a93beb8b7a2
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc6d57d501f0f100f069522e4b51666918168fa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="endswith-method-string-javascript"></a>Metodo endsWith Method (String) (JavaScript)
Restituisce un valore che indica se una stringa o una sottostringa termina con un'altra stringa specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
  
stringObj.endsWith(str, [, position]);  
```  
  
#### <a name="parameters"></a>Parametri  
 `stringObj`  
 Obbligatorio. Oggetto string da cercare.  
  
 `str`  
 Obbligatorio. Stringa di ricerca.  
  
 `position`  
 Parametro facoltativo. Posizione del primo carattere da cercare nell'oggetto string, partendo da 0.  
  
## <a name="return-value"></a>Valore restituito  
 Se la stringa che parte da `position` inizia con la stringa di ricerca, il metodo `endsWith` restituisce `true`. In caso contrario, restituisce `false`.  
  
## <a name="exceptions"></a>Eccezioni  
 Se `str` è `RegExp`, viene generata un'eccezione `TypeError`.  
  
## <a name="remarks"></a>Note  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]