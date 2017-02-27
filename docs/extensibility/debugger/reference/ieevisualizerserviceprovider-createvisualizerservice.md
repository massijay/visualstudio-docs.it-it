---
title: "IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerServiceProvider::CreateVisualizerService"
helpviewer_keywords: 
  - "Metodo IEEVisualizerServiceProvider::CreateVisualizerService"
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo crea un servizio del visualizzatore.  
  
## Sintassi  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```c#  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### Parametri  
 `binder`  
 \[in\]  [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) l'oggetto passato a [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 \[in\]  [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) L'oggetto passato a `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 \[in\]  [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) L'oggetto passato a `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 \[in\]  Un oggetto che implementa [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) l'interfaccia \(fornita dall'analizzatore di espressioni\).  
  
 `ppService`  
 \[out\]  il servizio creato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 `binder`, `pSymProv`e i parametri di tutti `pAddress` sono stati passati a `IDebugParsedExpression::EvaluateSync` il metodo.  `CreateVisualizerService` deve essere chiamato solo da `IDebugParsedExpression::EvaluateSync` come parte del supporto di un analizzatore di espressioni ai visualizzatori di tipi.  
  
## Vedere anche  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)