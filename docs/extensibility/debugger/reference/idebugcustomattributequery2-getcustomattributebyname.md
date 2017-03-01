---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
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
ms.openlocfilehash: bc1b59d4f13029a765f11dfd4fe3dbe12778d00c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Ottiene i byte di attributi personalizzati, dato il nome dell'attributo personalizzato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```c#  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszCustomAttributeName`  
 [in] Stringa contenente il nome dell'attributo personalizzato da cercare.  
  
 `ppBlob`  
 [in, out] Matrice che viene compilata con i byte di attributo personalizzato.  
  
 `pdwLen`  
 [in, out] Specifica il numero massimo di byte per restituire il `ppBlob` di matrice e restituisce il numero di byte effettivamente scritti nella matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se l'attributo personalizzato non esiste. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Impostare il `ppBlob` gli attributi di parametro con un valore null per restituire il numero di byte disponibili. Allocare una matrice, quindi passare la matrice in per il `ppBlob` parametro.  
  
 I byte di attributo rappresentano i dati non elaborati dell'attributo personalizzato.  
  
 Se il `ppBlob` e `pdwLen` i parametri vengono impostati su un valore null, questo metodo può essere utilizzato per determinare se esiste solo un attributo personalizzato. Un'alternativa più semplice, tuttavia, consiste nel chiamare il [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
