---
title: IDebugProperty3::DestroyObjectID | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::DestroyObjectID
helpviewer_keywords: IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ceae63b77f0797e0781318cfa362e735d995eb3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Elimina l'ID univoco associato a questa proprietà, che indica che il chiamante non sono più ritenute identificare questa proprietà in modo univoco da tutte le altre proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se il motore di debug non è necessaria supportare un ID univoco per una proprietà (perché già vengono rilevate in modo univoco internamente), quindi può semplicemente restituire `E_NOTIMPL` per questo metodo.  
  
 Gli ID univoci vengono creati con una chiamata al [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) metodo quando il chiamante desidera assicurarsi che questa proprietà viene identificata in modo univoco tra tutte le altre proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)