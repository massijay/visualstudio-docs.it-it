---
title: "IDebugDocumentContext2::GetSourceRange | Microsoft Docs"
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
  - "IDebugDocumentContext2::GetSourceRange"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetSourceRange"
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene l'intervallo del codice sorgente del contesto del documento.  
  
## Sintassi  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### Parametri  
 `pBegPosition`  
 \[in, out\]  [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Una struttura che verrà riempita con posizione iniziale.  Impostare questo argomento con un valore null se tali informazioni non sono necessarie.  
  
 `pEndPosition`  
 \[in, out\]  [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Una struttura che verrà riempita con posizione finale.  Impostare questo argomento con un valore null se tali informazioni non sono necessarie.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Un intervallo di origine è l'intero intervallo di codice sorgente, dall'istruzione corrente di nuovo immediatamente successivo all'istruzione precedente che codice fornito.  L'intervallo di origine in genere utilizzato per combinare le istruzioni originali, inclusi i commenti, con il codice della finestra disassembly.  
  
 Per ottenere l'intervallo solo per le istruzioni del codice contenute nel contesto del documento, chiamare [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) il metodo.  
  
## Vedere anche  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)