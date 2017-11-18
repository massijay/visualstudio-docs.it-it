---
title: IDebugProgram2::CauseBreak | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::CauseBreak
helpviewer_keywords: IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a58abdcf816896c0705a7ecce32ae82c9c8f16d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Le richieste che il programma di arresta l'esecuzione alla successiva ora di uno dei tentativi thread di esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) viene inviato l'evento quando viene quindi effettuato un tentativo eseguire codice dopo questo metodo viene chiamato.  
  
 Questo metodo è asincrono, in quanto il metodo restituisce immediatamente senza attendere necessariamente il blocco del programma.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)