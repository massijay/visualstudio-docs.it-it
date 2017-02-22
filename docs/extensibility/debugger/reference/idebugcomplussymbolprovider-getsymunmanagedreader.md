---
title: "IDebugComPlusSymbolProvider::GetSymUnmanagedReader | Microsoft Docs"
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
  - "IDebugComPlusSymbolProvider::GetSymUnmanagedReader"
  - "GetSymUnmanagedReader"
ms.assetid: 8f1c1627-217f-4405-8141-7a2eb80310a5
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugComPlusSymbolProvider::GetSymUnmanagedReader
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera il reader di simboli da utilizzare dal codice non gestito.  
  
## Sintassi  
  
```cpp#  
HRESULT GetSymUnmanagedReader(  
   ULONG32    ulAppDomainID,  
   GUID       guidModule,  
   IUnknown** ppSymUnmanagedReader  
);  
```  
  
```c#  
int GetSymUnmanagedReader(  
   uint       ulAppDomainID,  
   Guid       guidModule,  
   out object ppSymUnmanagedReader  
);  
```  
  
#### Parametri  
 `ulAppDomainID`  
 \[in\]  Identificatore del dominio applicazione.  
  
 `guidModule`  
 \[in\]  Identificatore univoco del modulo.  
  
 `ppSymUnmanagedReader`  
 \[out\]  Restituisce l'oggetto che rappresenta il reader di simboli.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto **di CDebugSymbolProvider** che espone [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) l'interfaccia.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetSymUnmanagedReader(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IUnknown ** ppSymUnmanagedReader  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetSymUnmanagedReader );  
  
    IfFailGo( GetModule( idModule, &pModule ) );  
    IfFailGo( pModule->GetSymReader((ISymUnmanagedReader**) ppSymUnmanagedReader) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetSymUnmanagedReader, hr );  
    return hr;  
}  
```  
  
## Vedere anche  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)