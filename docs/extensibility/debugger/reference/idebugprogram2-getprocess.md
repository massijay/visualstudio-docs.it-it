---
title: IDebugProgram2::GetProcess | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetProcess
helpviewer_keywords: IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6d085c149c72393f0179ad6b6b50334426777d9c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Ottenere il processo in esecuzione in questo programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppProcess`  
 [out] Restituisce il [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfaccia che rappresenta il processo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 A meno che non implementa un motore di debug (DE) il [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) interfaccia, l'implementazione del DE di questo metodo deve sempre restituire `E_NOTIMPL` perché un Germania può determinare quale processo è in esecuzione in e, pertanto non è possibile soddisfare un'implementazione di questo metodo.  
  
 Implementazione di `IDebugEngineLaunch2` interfaccia significa che la Germania necessario sapere come creare un processo; pertanto del DE attuazione di [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia è in grado di conoscere il processo è in esecuzione in.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)