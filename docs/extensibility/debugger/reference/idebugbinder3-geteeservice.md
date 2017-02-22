---
title: "IDebugBinder3::GetEEService | Microsoft Docs"
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
  - "IDebugBinder3::GetEEService"
helpviewer_keywords: 
  - "Metodo IDebugBinder3::GetEEService"
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetEEService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questo metodo restituisce un servizio richiesto.  
  
## Sintassi  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```c#  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### Parametri  
 `vendor`  
 \[in\]  `GUID` di un fornitore \(un valore null è accettabile\).  
  
 `language`  
 \[in\]  `GUID` di un linguaggio \(un valore null è accettabile\).  
  
 `iid`  
 \[in\]  `IID` del servizio da verificare.  
  
 `ppService`  
 \[out\]  Un'interfaccia al servizio richiesto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Passare `IID` per [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) l'interfaccia \(`IID_IEEVisualizerServiceProvider`\) per verificare se il servizio del visualizzatore del tipo è disponibile.  In caso affermativo, l'analizzatore di espressioni possibile ottenere [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) l'interfaccia per supportare i visualizzatori di tipi.  Per informazioni dettagliate, vedere [Visualizzazione e la visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md).  
  
## Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Visualizzazione e la visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)