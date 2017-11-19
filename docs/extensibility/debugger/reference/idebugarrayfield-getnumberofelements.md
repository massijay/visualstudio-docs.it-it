---
title: IDebugArrayField::GetNumberOfElements | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayField::GetNumberOfElements
helpviewer_keywords: IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30b85f22a433a457eb9813790eb0456ba7275c0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
Ottiene il numero di elementi nella matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetNumberOfElements(   
   DWORD* pdwNumElements  
);  
```  
  
```csharp  
int GetNumberOfElements(  
   out uint pdwNumElements  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwNumElements`  
 [out] Restituisce il numero di elementi nella matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il valore restituito è il numero totale di elementi nella matrice, indipendentemente dal numero di dimensioni.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)