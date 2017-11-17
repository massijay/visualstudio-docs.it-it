---
title: IDebugArrayObject::GetDimensions | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetDimensions
helpviewer_keywords: IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d516032e458bcc0f85c73c75a9147ff53fc0fff2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Ottiene le dimensioni della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwCount`  
 [in] Il numero di dimensioni da recuperare.  
  
 `dwDimensions`  
 [in, out] Matrice che viene compilata con le dimensioni di ciascuna dimensione. `dwCount`Specifica la dimensione massima del `dwDimensions` matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Una matrice multidimensionale può avere dimensioni diverse per ogni dimensione. Si consideri ad esempio la matrice tridimensionale `myarray[3][2][6]`, questo metodo restituisce 3, 2 e 6 di `dwDimensions` parametro nell'ordine specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)