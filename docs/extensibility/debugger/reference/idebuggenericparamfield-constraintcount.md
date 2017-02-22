---
title: "IDebugGenericParamField::ConstraintCount | Microsoft Docs"
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
  - "ConstraintCount"
  - "IDebugGenericParamField::ConstraintCount"
ms.assetid: 76bef0cb-8a3c-4ce5-87cc-1809de229f33
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugGenericParamField::ConstraintCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce il numero dei vincoli associati a questo parametro generico.  
  
## Sintassi  
  
```cpp#  
HRESULT ConstraintCount(  
   ULONG32* pcConst  
);  
```  
  
```c#  
int ConstraintCount(  
   ref uint pcConst  
);  
```  
  
#### Parametri  
 `pcConst`  
 \[in, out\]  Numero di vincoli associati a questo campo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto **di CDebugGenericParamFieldType** che espone [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) l'interfaccia.  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::ConstraintCount(ULONG32* pcConst)  
{  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<IMetaDataImport2> pMetadata2;  
    HCORENUM hEnum = 0;  
    ULONG cConst = 0;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::ConstraintCount );  
  
    IfFalseGo(pcConst, E_INVALIDARG );  
    *pcConst = 0;  
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );  
    IfFailGo( pMetadata->QueryInterface(IID_IMetaDataImport2, (void**)&pMetadata2) );  
    IfFailGo( pMetadata2->EnumGenericParamConstraints( &hEnum,  
              m_tokParam,  
              NULL,  
              0,  
              &cConst) );  
    IfFailGo( pMetadata->CountEnum(hEnum, &cConst) );  
    pMetadata->CloseEnum(hEnum);  
    hEnum = NULL;  
  
    *pcConst = cConst;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::ConstraintCount, hr );  
    return hr;  
}  
```  
  
## Vedere anche  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)