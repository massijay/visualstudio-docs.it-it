---
title: "IDebugProgram2::GetDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetDebugProperty"
helpviewer_keywords: 
  - "IDebugProgram2::GetDebugProperty"
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene le proprietà del programma.  
  
## Sintassi  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```c#  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### Parametri  
 `ppProperty`  
 \[out\]  Restituisce [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) un oggetto che rappresenta le proprietà del programma.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Le proprietà restituite dal metodo sono specifiche del programma.  Se il programma deve restituire più proprietà, quindi [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) l'oggetto restituito da questo metodo è un contenitore delle proprietà aggiuntive e di chiamare [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) il metodo restituisce un elenco di tutte le proprietà.  
  
 Un programma può esporre qualsiasi numero e tipo di proprietà aggiuntive che è possibile descrivere mediante l'interfaccia di `IDebugProperty2` .  Un IDE è possibile visualizzare le proprietà aggiuntive di programma mediante un'interfaccia utente generica del Visualizzatore proprietà.  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)