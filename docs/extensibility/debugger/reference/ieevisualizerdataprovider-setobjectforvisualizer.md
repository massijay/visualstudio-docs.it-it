---
title: "IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider::SetObjectForVisualizer"
helpviewer_keywords: 
  - "Metodo IEEVisualizerDataProvider::SetObjectForVisualizer"
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo converte l'oggetto che il visualizzatore rappresenta.  
  
## Sintassi  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```c#  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### Parametri  
 `pNewObject`  
 \[in\]  L'oggetto da impostare.  
  
 `error`  
 \[out\]  Se si è verificato un errore che imposta l'oggetto, l'oggetto di questa stringa il messaggio di errore.  
  
 `pException`  
 \[out\]  Se si è verificato un errore, l'oggetto di questo oggetto le informazioni sull'eccezione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Spetta al l'implementatore per determinare quali le informazioni sugli errori vengono restituite.  Tuttavia, è possibile che alcuni chiamante possono apparire solo per verificare se un oggetto eccezione è stato restituito per sapere che si è verificato un errore, pertanto questo metodo deve sempre restituire un oggetto eccezione se si è verificato un errore.  La stringa di errore deve essere fornita nel caso il chiamante desidera usarlo.  
  
## Vedere anche  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)