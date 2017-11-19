---
title: IDebugProcess2::Detach | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::Detach
helpviewer_keywords: IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37e642c8aa8709de28ea70d1a9d303877df25267
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Disconnette il debugger da questo processo scollegare tutte le applicazioni del processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Tutti i programmi e il processo di continuare l'esecuzione, ma non fanno più parte della sessione di debug. Al termine dell'operazione di scollegamento debug completo, non sono più presenti verranno inviati gli eventi per questo processo (e i relativi programmi).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)