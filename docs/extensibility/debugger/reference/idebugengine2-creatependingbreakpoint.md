---
title: "IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
helpviewer_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Creazione di un punto di interruzione in attesa nel motore di \(DE\) debug.  
  
## Sintassi  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```c#  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### Parametri  
 `pBPRequest`  
 \[in\]  [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) Un oggetto che descrive del punto di interruzione in sospeso da creare.  
  
 `ppPendingBP`  
 \[out\]  Restituisce [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) un oggetto che rappresenta il punto di interruzione in attesa.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  In genere restituisce `E_FAIL` se il parametro di `pBPRequest` non corrisponde a un linguaggio supportato da DE di se il parametro di `pBPRequest` non è valido o non è completo.  
  
## Note  
 Di un punto di interruzione in attesa è essenzialmente una raccolta di tutte le informazioni necessarie per associare un punto di interruzione nel codice.  Il punto di interruzione in attesa restituito da questo metodo non è associato al codice [Operazione di binding](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) finché non viene chiamato il metodo.  
  
 Per ciascun punto di interruzione in corsoutente, l'amministratore \(SDM\) di debug della sessione chiama questo metodo in ogni DE associato.  Spetta al DE per verificare che il punto di interruzione sia valido per i programmi in esecuzione in tale DE.  
  
 Quando che un utente ha impostato un punto di interruzione su una riga di codice, il DE è la possibilità di associare il punto di interruzione in corrispondenza più vicina nel documento corrispondente a tale codice.  In questo modo affinché l'utente imposti un punto di interruzione sulla prima riga dell'istruzione su più righe, ma associaultima riga \(dove il codice con attributi nelle informazioni di debug.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto semplice di `CProgram` .  L'implementazione Di DE di `IDebugEngine2::CreatePendingBreakpoint` potrebbe quindi inoltrare tutte le chiamate a questa implementazione del metodo da ogni programma.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Operazione di binding](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)