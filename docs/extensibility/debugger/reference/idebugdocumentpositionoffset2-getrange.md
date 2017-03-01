---
title: IDebugDocumentPositionOffset2::GetRange | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 6
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
ms.openlocfilehash: d14c212a3cb4499996ba6cf4d73d0b2fca73f7bc
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Recupera l'intervallo per la posizione del documento corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```c#  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwBegOffset`  
 [in, out] Offset per la posizione iniziale dell'intervallo. Impostare questo parametro su un valore null se queste informazioni non sono necessaria.  
  
 `pdwEndOffset`  
 [in, out] Offset per la posizione finale dell'intervallo. Impostare questo parametro su un valore null se queste informazioni non sono necessaria.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'intervallo specificato in una posizione di documento per un punto di interruzione di posizione è utilizzato dal motore di debug (DE) per la ricerca con un'istruzione che fornisce in realtà codice. Si consideri il codice di esempio seguente:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Riga 5 non contribuisce a nessun codice del programma sottoposto a debug. Se il debugger che imposta il punto di interruzione alla riga 5 desidera DE per eseguire la ricerca di un determinato periodo per la prima riga di codice, il debugger specificare un intervallo che include le righe aggiuntive candidato in cui un punto di interruzione può essere posizionato correttamente. Il DE sarebbe quindi la ricerca al tali righe finché non trovata una riga in grado di accettare un punto di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
