---
title: "IDebugMethodField::EnumArguments | Microsoft Docs"
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
  - "IDebugMethodField::EnumArguments"
helpviewer_keywords: 
  - "Metodo IDebugMethodField::EnumArguments"
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumeratore per il tipo di ciascun argomento obbligatorio per chiamare il metodo.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### Parametri  
 `ppParams`  
 \[out\]  Restituisce [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) un oggetto che rappresenta l'elenco di tipi di argomento.  Restituisce un valore null se non sono presenti argomenti.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK o restituisce S\_FALSE se non sono presenti argomenti.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Ogni elemento è [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) un oggetto che rappresenta i tipi dei parametri.  Chiamare [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) il metodo per recuperare le informazioni sul tipo di ogni parametro.  
  
 Se il nome del parametro è necessario con il tipo, quindi chiamare [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) il metodo.  
  
## Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)