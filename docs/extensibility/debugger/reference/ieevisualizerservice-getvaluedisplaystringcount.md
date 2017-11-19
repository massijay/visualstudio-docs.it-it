---
title: IEEVisualizerService::GetValueDisplayStringCount | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6fd3d05935c2edaeff723dc979764faf04d61c10
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Recupera il numero di stringhe di valori da visualizzare per la proprietà specificata o il campo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```csharp  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `displayKind`  
 [in] Valore di [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) enumerazione.  
  
 `propertyOrField`  
 [in] Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia che rappresenta una proprietà o campo.  
  
 `pcelt`  
 [out] Restituisce il numero di stringhe di valore da visualizzare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)