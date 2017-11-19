---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords: IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76a901401e854611cc987ac5c0cf8eeabb8dfd53
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Questo metodo modifica l'oggetto che rappresenta il visualizzatore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pNewObject`  
 [in] Oggetto da impostare.  
  
 `error`  
 [out] Se si è verificato un errore durante l'impostazione dell'oggetto, questa stringa contiene il messaggio di errore.  
  
 `pException`  
 [out] Se si è verificato un errore, questo oggetto contiene le informazioni sull'eccezione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 È responsabilità dell'implementatore per determinare le modalità di restituzione di informazioni sull'errore. Tuttavia, è possibile che alcuni chiamanti possano solo aspetto per vedere se è stato restituito un oggetto eccezione conoscere si è verificato un errore, in modo da questo metodo deve sempre restituire un oggetto eccezione, se si è verificato un errore. La stringa di errore deve essere presenti anche nel caso in cui il chiamante vuole rendere utilizzarlo.  
  
## <a name="see-also"></a>Vedere anche  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)