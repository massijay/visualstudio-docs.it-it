---
title: "IDebugDocumentContext2::Seek | Microsoft Docs"
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
  - "IDebugDocumentContext2::Seek"
helpviewer_keywords: 
  - "IDebugDocumentContext2::Seek"
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::Seek
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Consente di spostare il contesto del documento da un numero specificato di istruzioni o righe.  
  
## Sintassi  
  
```cpp#  
HRESULT Seek(   
   int                      nCount,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```cpp#  
int Seek(   
   int                        nCount,  
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### Parametri  
 `nCount`  
 \[in\]  Il numero di istruzioni o righe da spostare avanti, a seconda del contesto del documento.  
  
 `ppDocContext`  
 \[out\]  restituisce un nuovo [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) oggetto con la nuova posizione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)