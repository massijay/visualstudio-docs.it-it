---
title: "IDebugGenericParamField::GetFlags | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetFlags"
  - "IDebugGenericParamField::GetFlags"
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugGenericParamField::GetFlags
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

recupera i flag per questo parametro generico.  
  
## Sintassi  
  
```cpp#  
HRESULT GetFlags(  
   DWORD* pdwFlags  
);  
```  
  
```c#  
int GetFlags(  
   ref uint pdwFlags  
);  
```  
  
#### Parametri  
 `pdwFlags`  
 \[out\]  restituisce i flag per questo parametro generico.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questi flag contengono informazioni sui diversi vincoli speciali.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto **di CDebugGenericParamFieldType** che espone [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) l'interfaccia.  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );  
  
    IfFalseGo( pdwFlags, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pdwFlags = m_dwFlags;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );  
    return hr;  
}  
```  
  
## Vedere anche  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)