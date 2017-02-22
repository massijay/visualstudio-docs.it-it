---
title: "IDebugDocumentContext2::GetStatementRange | Microsoft Docs"
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
  - "IDebugDocumentContext2::GetStatementRange"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetStatementRange"
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::GetStatementRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene l'intervallo dell'istruzione del file del contesto del documento.  
  
## Sintassi  
  
```cpp#  
HRESULT GetStatementRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetStatementRange(   
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
 Un intervallo di istruzione è l'intervallo delle righe che dispongono del codice a cui questo contesto di documento fa riferimento.  
  
 Per ottenere l'intervallo del codice sorgente \(commenti incluse\) nel contesto del documento, chiamare [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) il metodo.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto semplice di `CDebugContext` che espone [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) l'interfaccia.  Questo esempio consente di riempire la posizione finale solo se la posizione iniziale non è un valore null.  
  
```cpp#  
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,  
                                         TEXT_POSITION* pEndPosition)    
{    
   HRESULT hr;    
  
   // Check for a valid beginning position argument pointer.    
   if (pBegPosition)    
   {    
      // Copy the member TEXT_POSITION into the local pBegPosition.    
      memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));    
  
      // Check for a valid ending position argument pointer.   
     if (pEndPosition)    
      {    
         // Copy the member TEXT_POSITION into the local pEndPosition.    
         memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));    
      }    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## Vedere anche  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)