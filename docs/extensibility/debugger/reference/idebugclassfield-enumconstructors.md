---
title: IDebugClassField::EnumConstructors | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::EnumConstructors
helpviewer_keywords: IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24ae27acb2dd78b086a8b94e28c3de705cd710ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Crea un enumeratore per i costruttori per questa classe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cMatch`  
 [in] Un valore di [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) enumerazione che specifica il tipo di costruttori per l'enumerazione.  
  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco di costruttori. Restituisce un valore null se non sono presenti costruttori.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK o S_FALSE se non sono presenti costruttori. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ogni elemento dell'enumerazione è un [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) oggetto che descrive un metodo del costruttore.  
  
 L'elenco di costruttori in genere non include i costruttori predefiniti forniti da un compilatore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)