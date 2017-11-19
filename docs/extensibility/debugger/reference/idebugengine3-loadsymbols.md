---
title: IDebugEngine3::LoadSymbols | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3::LoadSymbols
helpviewer_keywords: IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad486256b194ae0f03ed3fe41c23a71f2f9159c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Simboli Carica (se necessario) per tutti i moduli in fase di debug per il motore di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```csharp  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 In questo modo caricati simboli di debug per tutti i moduli a cui fa riferimento questo motore di debug. I simboli vengono caricati solo se non sono già stati caricati. Simboli vengono eseguita la ricerca nei percorsi di set da una chiamata a [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)