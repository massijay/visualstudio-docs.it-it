---
title: IDebugExpressionEvaluator2::PreloadModules | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::PreloadModules
- PreloadModules
ms.assetid: bcf9b968-ee14-4a92-88ad-926268a44e03
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eaceac744b06a44e3ef73de6cc9eda7255e59cb8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluator2preloadmodules"></a>IDebugExpressionEvaluator2::PreloadModules
Precarica i moduli designati dal provider di simbolo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT PreloadModules (  
   IDebugSymbolProvider* pSym  
);  
```  
  
```csharp  
int PreloadModules (  
   IDebugSymbolProvider pSym  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pSym`  
 [in] Provider di simboli per il quale verranno precaricati i moduli.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo facoltativo viene utilizzato quando si collega un processo di hosting. L'analizzatore di Espressioni fornisce la possibilità di 'riscaldamento' come parte della connessione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un **ExpressionEvaluatorPackage** oggetto che espone il [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) interfaccia.  
  
```cpp  
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
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)