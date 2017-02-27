---
title: "IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
helpviewer_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea una copia di un oggetto dati specifico dell'analizzatore di \(EE\) espressioni.  
  
## Sintassi  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### Parametri  
 `dataIn`  
 \[in\]  [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Un oggetto contenente i dati da copiare.  
  
 `dataOut`  
 \[out\]  restituisce un nuovo oggetto di `IEEDataStorage` .  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo viene [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) fornito un oggetto che rappresenta una matrice di byte.  Questo oggetto dati in ingresso non viene in genere distribuito dall'EE.  Tuttavia, l'oggetto restituito da questo metodo viene implementato sempre dall'EE, in cui sarà l'EE implementare l'interfaccia di `IEEDataStorage` qualsiasi classe è desiderata.  
  
 Si noti che i dati forniti dall'oggetto in ingresso di `IEEDataStorage` devono essere gli stessi dati nell'oggetto in uscita di `IEEDataStorage` .  
  
## Vedere anche  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)