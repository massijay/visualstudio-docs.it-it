---
title: "IDebugGenericParamField::GetNameOfFormalParam | Microsoft Docs"
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
  - "IDebugGenericParamField::GetNameOfFormalParam"
  - "GetNameOfFormalParam"
ms.assetid: 05032a83-49ce-4007-b5d6-7b56945b956c
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugGenericParamField::GetNameOfFormalParam
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera il nome del parametro generico.  
  
## Sintassi  
  
```cpp#  
HRESULT GetNameOfFormalParam (  
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetNameOfFormalParam (  
   string pbstrName  
);  
```  
  
#### Parametri  
 `pbstrName`  
 \[out\]  Nome del parametro generico.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto **di CDebugGenericParamFieldType** che espone [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) l'interfaccia.  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetNameOfFormalParam(BSTR *pbstrName)  
{  
    HRESULT hr = S_OK;  
    CComBSTR bstrName;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetNameOfFormalParam );  
  
    IfFalseGo( pbstrName, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    IfNullGo( *pbstrName = SysAllocString(m_bstrName), E_OUTOFMEMORY );  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetNameOfFormalParam, hr );  
    return hr;  
}  
```  
  
## Vedere anche  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)