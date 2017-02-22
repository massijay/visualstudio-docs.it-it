---
title: "BP_LOCATION_CODE_ADDRESS | Microsoft Docs"
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
  - "BP_LOCATION_CODE_ADDRESS"
helpviewer_keywords: 
  - "Struttura BP_LOCATION_CODE_ADDRESS"
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION_CODE_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Viene descritta la posizione di un punto di interruzione a un indirizzo nel codice.  
  
## Sintassi  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_ADDRESS {   
   BSTR bstrContext;  
   BSTR bstrModuleUrl;  
   BSTR bstrFunction;  
   BSTR bstrAddress;  
} BP_LOCATION_CODE_ADDRESS;  
```  
  
## Membri  
 `bstrContext`  
 Il contesto del punto di interruzione, in genere un nome di funzione o di metodo come indicato in uno stack di chiamate.  
  
 `bstrModuleUrl`  
 L'URL del modulo che contiene il punto di interruzione.  
  
 `bstrFunction`  
 Il nome della funzione che contiene il punto di interruzione.  
  
 `bstrAddress`  
 L'indirizzo del punto di interruzione, che viene analizzato da un analizzatore di espressioni per l'associazione [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) a un oggetto.  
  
## Note  
 Questa struttura è un membro [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) della struttura come parte di unione.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)