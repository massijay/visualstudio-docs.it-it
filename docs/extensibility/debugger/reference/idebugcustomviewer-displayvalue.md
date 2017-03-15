---
title: "IDebugCustomViewer::DisplayValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer::DisplayValue"
helpviewer_keywords: 
  - "IDebugCustomViewer::DisplayValue"
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo viene chiamato per visualizzare il valore specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```c#  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### Parametri  
 `hwnd`  
 \[in\]  finestra padre  
  
 `dwID`  
 \[in\]  ID per i visualizzatori personalizzati che supportano più di un tipo.  
  
 `pHostServices`  
 \[in\] Riservato.  Sempre impostato su null.  
  
 `pDebugProperty`  
 \[in\]  Collegare che può essere utilizzato per recuperare il valore da visualizzare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce il codice di errore.  
  
## Note  
 La visualizzazione è “modale„ in quanto questo metodo viene creata la finestra necessaria, viene visualizzato il valore, attenderà l'input e chiudere la finestra, tutti prima di restituire il chiamante.  Ciò significa che il metodo deve gestire tutti gli aspetti della visualizzazione del valore della proprietà, dalla creazione di una finestra di output, di attendere l'input dell'utente, l'eliminazione permanente la finestra.  
  
 Per supportare modificare il valore dell'oggetto specificato [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , è possibile utilizzare [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) il metodo \- se il valore può essere espresso come stringa.  In caso contrario, è necessario creare un interfaccia\-esclusiva analizzatore di espressioni che implementa questo `DisplayValue` metodo\-sullo stesso oggetto che implementa l'interfaccia di `IDebugProperty3` .  Questa interfaccia fornisce i metodi per modificare i dati di una dimensione o della complessità arbitraria.  
  
## Vedere anche  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)