---
title: IDebugArrayObject::GetElement | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ddfb54b0bf5d6adb1721095fe0c6e748aea024e5
ms.lasthandoff: 02/22/2017

---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Ottiene un elemento della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```c#  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwIndex`  
 [in] L'indice di elemento.  
  
 `ppElement`  
 [out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia che rappresenta l'elemento.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo considera tutti gli elementi di un oggetto matrice di una matrice unidimensionale, anche se l'oggetto matrice multidimensionale. Si consideri ad esempio la matrice `myarray[3][2][6]` e `dwIndex` parametro pari a 20, questo metodo restituisce l'elemento da `myarray[1][1][2]`e un `dwIndex` parametro 21 restituisce l'elemento da `myarray[1][1][3]`. Utilizzare il [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) metodo per determinare il numero totale di elementi nella matrice.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)