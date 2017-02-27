---
title: "IDebugDocumentText2::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentText2::GetSize"
helpviewer_keywords: 
  - "IDebugDocumentText2::GetSize"
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentText2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera la dimensione del testo in questa posizione nel documento.  
  
## Sintassi  
  
```cpp#  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```c#  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### Parametri  
 `pcNumLines`  
 \[out\]  Restituisce il numero di righe di testo.  
  
 `pcNumChars`  
 \[out\]  restituisce il numero di caratteri di testo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 \[C\+\+ solo\] se un particolare valore non è previsto, passare NULL per il parametro.  
  
 \[Solo c\#\] entrambi i parametri devono essere specificati.  
  
## Vedere anche  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)