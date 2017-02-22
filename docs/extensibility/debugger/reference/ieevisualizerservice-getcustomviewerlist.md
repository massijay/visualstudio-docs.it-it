---
title: "IEEVisualizerService::GetCustomViewerList | Microsoft Docs"
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
  - "IEEVisualizerService::GetCustomViewerList"
helpviewer_keywords: 
  - "Metodo IEEVisualizerService::GetCustomViewerList"
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerService::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo restituisce un elenco di visualizzatori di tipi che questo servizio è a conoscenza.  
  
## Sintassi  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```c#  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### Parametri  
 `celtSkip`  
 \[in\]  Numero di visualizzatori da ignorare.  
  
 `celRequested`  
 \[in\]  Numero di visualizzatori da recuperare \(anche specifica la dimensione della matrice di `rgViewers` \).  
  
 `rgViewers`  
 \[in, out\]  Matrice [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) di strutture da riempire.  
  
 `pceltFetched`  
 \[out\]  Numero di visualizzatori effettivamente recuperate.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) passa la richiesta a questo metodo come parte del supporto per i visualizzatori di tipi.  Se l'analizzatore di espressioni vengono forniti i visualizzatori personalizzati per lo stesso tipo, possibile collegare le strutture in modo appropriato riempite\-fuori [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) per i visualizzatori personalizzati all'elenco.  Assicurarsi che [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) riflette i visualizzatori aggiuntivi.  
  
 Vedere [Tipo visualizzatore e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) per informazioni dettagliate sulle differenze tra i visualizzatori e i visualizzatori.  
  
## Vedere anche  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)   
 [Tipo visualizzatore e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)