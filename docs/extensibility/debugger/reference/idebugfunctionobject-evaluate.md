---
title: IDebugFunctionObject::Evaluate | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugFunctionObject::Evaluate
helpviewer_keywords: IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4eb9140ae74cd758525dba30fd4b4da49d82db9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Chiama la funzione e restituisce il valore risultante come oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppParams`  
 [in] Matrice di [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) gli oggetti che rappresentano i parametri di input. Ciascuno di questi parametri è stato creato con uno del `Create` metodi di [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.  
  
 `dwParams`  
 [in] Il numero di parametri in di `ppParams` matrice.  
  
 `dwTimeout`  
 [in] Specifica il tempo massimo, in millisecondi di attesa prima della restituzione da questo metodo. Utilizzare `INFINITE` per un'attesa indefinita.  
  
 `ppResult`  
 [out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta il valore della funzione come oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo configura ed esegue una chiamata alla funzione rappresentata dal [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)