---
title: "IDebugDocumentPosition2::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetRange"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetRange"
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene l'intervallo per questa posizione del documento.  
  
## Sintassi  
  
```cpp#  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetRange(   
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
 L'intervallo specificato in un percorso del documento per un punto di interruzione di posizione viene utilizzato dal motore \(DE\) di debug per eseguire la ricerca un'istruzione che effettivamente fornisce il codice.  Si consideri il codice di esempio seguente:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 La riga 5 non fornisce codice al programma sottoposto a debug.  Se il debugger che imposta un punto di interruzione 5 in linea desidera un DE per eseguire la ricerca della somma la prima riga che fornisce il codice, il debugger specificherebbe un intervallo che includa altre righe del candidato in cui un punto di interruzione può essere correttamente essere inserito.  Il DE quindi verrebbero utilizzati in avanti nelle righe finché non fondasse una riga che accetti un punto di interruzione.  
  
## Vedere anche  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)