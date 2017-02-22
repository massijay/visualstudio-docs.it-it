---
title: "IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs"
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
  - "IPropertyProxyEESide::InitSourceDataProvider"
helpviewer_keywords: 
  - "IPropertyProxyEESide::InitSourceDataProvider"
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide::InitSourceDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Inizializza i dati di origine per questo oggetto e restituisce un oggetto che contiene i dati.  
  
## Sintassi  
  
```cpp#  
HRESULT InitSourceDataProvider(  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int InitSourceDataProvider(  
   out IEEDataStorage dataOut  
);  
```  
  
#### Parametri  
 `dataOut`  
 \[out\]  restituisce [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) un oggetto  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo esegue qualsiasi è necessario inizializzare un oggetto in modo che possa restituire [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) un'interfaccia nei dati dell'oggetto.  In questo modo i dati dell'oggetto da visualizzare e, se consentita, modificati da un visualizzatore del tipo.  
  
## Vedere anche  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)