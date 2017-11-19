---
title: IDebugPortSupplier2::RemovePort | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier2::RemovePort
helpviewer_keywords: IDebugPortSupplier2::RemovePort
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b18c0e77f8a25bbe49a120b39fd0c57d9c549895
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplier2removeport"></a>IDebugPortSupplier2::RemovePort
Rimuove una porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT RemovePort(   
   IDebugPort2* pPort  
);  
```  
  
```csharp  
int RemovePort(   
   IDebugPort2 pPort  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pPort`  
 [in] Un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) oggetto che rappresenta la porta da rimuovere.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo rimuove la porta dall'elenco di porte attive interno del fornitore porta.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)