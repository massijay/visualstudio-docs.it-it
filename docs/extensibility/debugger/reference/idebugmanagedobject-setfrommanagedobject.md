---
title: IDebugManagedObject::SetFromManagedObject | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugManagedObject::SetFromManagedObject
helpviewer_keywords: IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a3f73236b45edea7a9dea003a1f3604669eb3739
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Imposta il valore dell'istanza dell'oggetto della classe di valore dall'istanza della classe di valori fornita come parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pManagedObject`  
 [in] Un'interfaccia che rappresenta l'oggetto gestito che contiene il nuovo valore.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene utilizzato per modificare l'oggetto gestito, come rappresentato dal [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)