---
title: IDebugObject::IsEqual | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 9
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
ms.openlocfilehash: 9780a18ff72058a90739c421061fabd9ce8520e1
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Confronta un oggetto con questo oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pObject`  
 [in] Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto che rappresenta l'oggetto da confrontare.  
  
 `pfIsEqual`  
 [out] Restituisce diverso da zero (`TRUE`) se i valori degli oggetti sono uguali; in caso contrario, restituisce zero (`FALSE`).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In genere, questo metodo può confrontare gli indirizzi dei valori rappresentati dal `pObject` parametro e questo [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto; se gli indirizzi sono uguali, gli oggetti possono essere considerati uguali.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
