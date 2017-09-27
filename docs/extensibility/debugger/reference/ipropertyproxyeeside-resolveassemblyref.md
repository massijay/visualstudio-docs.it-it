---
title: IPropertyProxyEESide::ResolveAssemblyRef | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: e71bb5aa2954c609cff4a3afbfba981bade3122c
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
Determina la posizione del riferimento all'assembly gestito specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT ResolveAssemblyRef(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  assemLocation,  
   ASSEMBLYLOCRESOLUTION* alr  
);  
```  
  
```csharp  
int ResolveAssemblyRef(  
   ref string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     assemLocation,  
   out enum_ASSEMBLYLOCRESOLUTION alr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `assemName`  
 [in] Nome dell'assembly da risolvere.  
  
 `assemBytes`  
 [out] Restituisce un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto contenente i byte dell'assembly associati al riferimento.  
  
 `assemPdb`  
 [out] Restituisce un `IEEDataStorage` oggetto contenente il simbolo di archiviazione i dati associati a questo riferimento.  
  
 `assemLocation`  
 [out] Restituisce il percorso di questo riferimento.  
  
 `alr`  
 [out] Restituisce un valore di [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) enumerazione che indica la posizione di assembly di questo riferimento.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo non è in genere implementato tramite un analizzatore di espressioni personalizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
