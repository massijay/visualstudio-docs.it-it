---
title: "IDebugExpressionEvaluator2::PreloadModules | Microsoft Docs"
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
  - "IDebugExpressionEvaluator2::PreloadModules"
  - "PreloadModules"
ms.assetid: bcf9b968-ee14-4a92-88ad-926268a44e03
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator2::PreloadModules
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Precarica i moduli indicati dal provider specificato del simbolo.  
  
## Sintassi  
  
```cpp#  
HRESULT PreloadModules (  
   IDebugSymbolProvider* pSym  
);  
```  
  
```c#  
int PreloadModules (  
   IDebugSymbolProvider pSym  
);  
```  
  
#### Parametri  
 `pSym`  
 \[in\]  Il provider dei simboli per il quale i moduli viene precaricato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo facoltativo viene utilizzato durante la disconnessione del processo di hosting.  Fornisce all'EE una probabilità “scaldarsi„ come parte della connessione.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto **di ExpressionEvaluatorPackage** che espone [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) l'interfaccia.  
  
```cpp#  
STDMETHODIMP ExpressionEvaluatorPackage::PreloadModules  
(  
    IDebugSymbolProvider *pSym  
)  
{  
    HRESULT hr = NOERROR;  
    RuntimeMemberDescriptor  * prtMemberDesc;  
    RuntimeClassDescriptor *prtClassDesc;  
    CComPtr<IDebugClassField> pClassField;  
    IfFalseGo(pSym,E_INVALIDARG);  
  
    prtMemberDesc = &(g_rgRTLangMembers[StandardModuleAttributeCtor]);  
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);  
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);  
  
    pClassField = NULL;  
    prtMemberDesc = &(g_rgRTLangMembers[LoadAssembly]);  
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);  
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);  
  
Error:  
    return hr;  
}  
```  
  
## Vedere anche  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)