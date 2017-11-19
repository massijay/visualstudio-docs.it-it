---
title: IDebugClassField::DoesInterfaceExist | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::DoesInterfaceExist
helpviewer_keywords: IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07a4760064003a45af55aa747192e044edca8e0c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Determina se un'interfaccia specifica è definita nella classe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszInterfaceName`  
 [in] Stringa contenente il nome dell'interfaccia da cercare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK, restituisce S_FALSE se l'interfaccia non esiste. in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In effetti, questo metodo ottiene un'enumerazione di tutte le interfacce e Cerca nell'elenco per l'interfaccia corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)