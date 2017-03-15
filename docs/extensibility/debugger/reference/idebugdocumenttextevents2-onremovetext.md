---
title: "IDebugDocumentTextEvents2::onRemoveText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2::OnRemoveText"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents2::onRemoveText"
ms.assetid: 1ebeabb2-52a1-4ccc-83cd-9ae7c3541783
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentTextEvents2::onRemoveText
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Notifica al pacchetto di debug che il testo è stato rimosso dal documento.  
  
## Sintassi  
  
```cpp#  
HRESULT onRemoveText(   
   TEXT_POSITION pos,  
   DWORD         dwNumToRemove  
);  
```  
  
```c#  
int onRemoveText(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToRemove  
);  
```  
  
#### Parametri  
 `pos`  
 \[in\]  [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) una struttura che indica dove il testo è stato rimosso.  
  
 `dwNumToRemove`  
 \[in\]  specifica il numero di caratteri di testo che è stato rimosso.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)