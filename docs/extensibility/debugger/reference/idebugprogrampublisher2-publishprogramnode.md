---
title: IDebugProgramPublisher2::PublishProgramNode | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramPublisher2::PublishProgramNode
helpviewer_keywords: IDebugProgramPublisher2::PublishProgramNode
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 49b510ec131a58778941ae925120fb58097b1db7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogrampublisher2publishprogramnode"></a>IDebugProgramPublisher2::PublishProgramNode
Rende un nodo di programma disponibile per uso dai motori di debug (DEs) e la sessione di debug manager (SDM).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT PublishProgramNode(  
   IDebugProgramNode2 *pProgramNode  
);  
```  
  
```csharp  
int PublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pProgramNode`  
 [in] Un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto che rappresenta il nodo di programma per rendere disponibili.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo consente di cercare informazioni prima di selezionare e li avvio per il debug.  
  
 Per rimuovere un nodo di programma da disponibilità, chiamare il [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)