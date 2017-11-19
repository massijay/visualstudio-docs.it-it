---
title: IDebugEngineProgram2::WatchForThreadStep | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords: IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 473deca83bea9e2fea9c52d2836291790def5804
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Verifica la presenza di esecuzione (o arresta controllo per l'esecuzione) a cui si verificano sul thread specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```csharp  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pOriginatingProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma viene eseguito.  
  
 `dwTid`  
 [in] Specifica l'identificatore del thread da controllare.  
  
 `fWatch`  
 [in] Diverso da zero (`TRUE`) significa iniziare la visione per l'esecuzione sul thread identificato da `dwTid`; in caso contrario, zero (`FALSE`) significa interruzione il controllo per l'esecuzione in `dwTid`.  
  
 `dwFrame`  
 [in] Specifica un indice di frame che controlla il tipo di passaggio. Quando questo valore è zero (0), il tipo di passaggio è "Esegui istruzione" e il programma deve essere interrotta ogni volta che il thread è identificato da `dwTid` esegue. Quando `dwFrame` è diverso da zero, il tipo di passaggio è "Esegui istruzione/routine" e il programma deve essere arrestata solo se il thread è identificato da `dwTid` è in esecuzione in un frame il cui indice è uguale o superiore nello stack di `dwFrame`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Quando i passaggi da un programma, identificato dal gestore di sessione di debug (SDM) il `pOriginatingProgram` parametro, invia una notifica a tutti gli altri programmi collegati chiamando questo metodo.  
  
 Questo metodo è applicabile solo per l'esecuzione di istruzioni stesso thread.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)