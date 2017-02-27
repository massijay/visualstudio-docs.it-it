---
title: "IDebugMethodField::EnumParameters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumParameters"
helpviewer_keywords: 
  - "Metodo IDebugMethodField::EnumParameters"
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumeratore per i parametri del metodo.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### Parametri  
 `ppParams`  
 \[out\]  Restituisce [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) un oggetto che rappresenta l'elenco dei parametri al metodo; in caso contrario, restituisce un valore null se non vi sono parametri.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK o restituisce S\_FALSE se non vi sono parametri.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Ogni elemento è [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) un oggetto che rappresenta i diversi tipi di parametri.  Chiamare [GetKind](../Topic/IDebugField::GetKind.md) il metodo su ciascun oggetto per determinare esattamente il tipo di parametro l'oggetto rappresenta.  
  
 Un parametro include sia il nome della variabile del tipo.  Il primo parametro al metodo della classe è in genere “this„ puntatore.  
  
 Se solo i tipi dei parametri è necessari, chiamare [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) il metodo.  
  
## Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)