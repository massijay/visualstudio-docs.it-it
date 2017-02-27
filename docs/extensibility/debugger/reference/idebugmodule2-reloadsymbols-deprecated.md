---
title: "IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2::ReloadSymbols"
helpviewer_keywords: 
  - "Metodo IDebugModule2::ReloadSymbols"
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

OBSOLETO.  NOT UTILIZZARE.  Ricaricare i simboli per questo modulo.  
  
## Sintassi  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```c#  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### Parametri  
 `pszUrlToSymbols`  
 \[in\]  Il percorso all'archivio simboli.  
  
 `pbstrDebugMessage`  
 \[out\]  Restituisce un messaggio informativo, ad esempio lo stato o un messaggio di errore, che viene visualizzata a destra del nome del modulo nella finestra moduli.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Il modulo di debug deve sempre restituire `E_FAIL`.  
  
## Note  
 Questo metodo non è più supportato.  Implementare [LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md) il metodo.  
  
## Vedere anche  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)