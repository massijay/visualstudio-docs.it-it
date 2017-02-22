---
title: "IDebugActivateDocumentEvent2::GetDocumentContext | Microsoft Docs"
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
  - "IDebugActivateDocumentEvent2::GetDocumentContext"
helpviewer_keywords: 
  - "Metodo GetDocumentContext"
  - "Metodo IDebugActivateDocumentEvent2::GetDocumentContext"
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugActivateDocumentEvent2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il contesto del documento che specifica la posizione del documento a cui deve essere effettuato ad attivo dal package di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```c#  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### Parametri  
 `ppDocContext`  
 \[out\]  Restituisce [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) un oggetto che rappresenta una posizione in un documento del file di origine.  
  
## Note  
 Questo percorso può essere utilizzata per mostrare il cursore, ad esempio.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)