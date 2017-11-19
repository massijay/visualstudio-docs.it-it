---
title: IDebugMethodField::EnumArguments | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::EnumArguments
helpviewer_keywords: IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d500e5bedbd284c15430ab65e9477d4a3a404eaf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Crea un enumeratore per il tipo di ogni argomento è necessario chiamare il metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppParams`  
 [out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco dei tipi di argomento. Restituisce un valore null se non sono presenti argomenti.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK o S_FALSE se non sono presenti argomenti. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ogni elemento è un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto che rappresenta i tipi di ogni parametro. Chiamare il [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metodo per recuperare informazioni sul tipo di ogni parametro.  
  
 Se è necessario specificare il nome del parametro insieme al tipo, quindi chiamare il [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)