---
title: "IDebugProcess3::DisableENC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::DisableENC"
helpviewer_keywords: 
  - "IDebugProcess3::DisableENC"
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo in modo esplicito disabilitare Modifica e continuazione su questo processo e in tutti i programmi che contiene.  Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## Sintassi  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```c#  
   EncUnavailableReason reason  
);  
```  
  
#### Parametri  
 `reason`  
 \[in\]  Un valore [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) dell'enumerazione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, codice di errore restituito.  
  
> [!NOTE]
>  Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## Note  
 Una volta che la Modifica e continuazione viene disabilitata per un processo, può essere riabilitatoe solo riavviando il processo.  
  
## Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)