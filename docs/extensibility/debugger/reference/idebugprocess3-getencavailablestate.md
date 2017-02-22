---
title: "IDebugProcess3::GetENCAvailableState | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::GetENCAvailableState"
helpviewer_keywords: 
  - "IDebugProcess3::GetENCAvailableState"
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::GetENCAvailableState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo ottiene lo stato corrente di Modifica e continuazione del processo.  Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## Sintassi  
  
```cpp  
HRESULT GetENCAvailableState(  
   EncUnavailableReason* pReason  
);  
```  
  
```c#  
int GetENCAvailableState(  
   EncUnavailableReason[] pReason  
);  
```  
  
#### Parametri  
 `pReason`  
 \[out\]  Un valore [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) dell'enumerazione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, codice di errore restituito.  
  
> [!NOTE]
>  Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## Note  
 Questo stato può essere influenzato da [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).  
  
## Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)