---
title: "IPropertyProxyProvider::GetPropertyProxy | Microsoft Docs"
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
  - "IPropertyProxyProvider::GetPropertyProxy"
helpviewer_keywords: 
  - "IPropertyProxyProvider::GetPropertyProxy"
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyProvider::GetPropertyProxy
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera l'interfaccia del proxy della proprietà per l'identificazione specificata del proxy  
  
## Sintassi  
  
```cpp#  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```c#  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### Parametri  
 `dwID`  
 \[in\]  ID del proxy previsto della proprietà.  
  
 `proxy`  
 \[out\]  restituisce [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) un oggetto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Per supportare i visualizzatori esterno del tipo, questo metodo in genere inoltra la chiamata [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) al metodo.  Vedere [Visualizzazione e la visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate sullo IEEVisualizerService viene ottenuto.  
  
## Vedere anche  
 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualizzazione e la visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)