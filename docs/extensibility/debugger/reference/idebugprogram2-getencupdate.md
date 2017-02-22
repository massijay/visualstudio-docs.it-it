---
title: "IDebugProgram2::GetENCUpdate | Microsoft Docs"
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
  - "IDebugProgram2::GetENCUpdate"
helpviewer_keywords: 
  - "IDebugProgram2::GetENCUpdate"
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::GetENCUpdate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo ottiene l'aggiornamento di Modifica e continuazione \(ENC\) per il programma.  Il modulo di debug personalizzato restituisce sempre `E_NOTIMPL`.  
  
## Sintassi  
  
```cpp#  
HRESULT GetENCUpdate(   
   IUnknown** ppUpdate  
);  
```  
  
```c#  
int GetENCUpdate(  
   out object ppUpdate  
);  
```  
  
#### Parametri  
 `ppUpdate`  
 \[out\]  Restituisce un'interfaccia interna che può essere utilizzata per aggiornare il programma.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
> [!NOTE]
>  Il modulo di debug personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)