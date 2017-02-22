---
title: "IDebugEngine2::GetEngineID | Microsoft Docs"
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
  - "IDebugEngine2::GetEngineID"
helpviewer_keywords: 
  - "IDebugEngine2::GetEngineID"
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::GetEngineID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il GUID del motore di \(DE\) debug.  
  
## Sintassi  
  
```cpp#  
HRESULT GetEngineID(   
   GUID* pguidEngine  
);  
```  
  
```c#  
int GetEngineID(   
   out Guid pguidEngine  
);  
```  
  
#### Parametri  
 `pguidEngine`  
 \[out\]  Restituisce il GUID di DE.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Alcuni esempi di GUID tipici comprendono `guidScriptEng`, `guidNativeEng`, o `guidSQLEng`.  I nuovi motori di debug creeranno il proprio GUID per l'identificazione.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto semplice di `CEngine` che implementa [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) l'interfaccia.  
  
```cpp#  
HRESULT CEngine::GetEngineId(GUID *pguidEngine){    
   if (pguidEngine) {    
      // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.    
      // Other languages would require their own guidDifferentEngine to be  
      //defined in the Batdbg.idl file.    
      *pguidEngine = guidBatEng;    
      return NOERROR; // This is typically S_OK.    
   } else {  
      return E_INVALIDARG;    
   }    
}    
```  
  
## Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)