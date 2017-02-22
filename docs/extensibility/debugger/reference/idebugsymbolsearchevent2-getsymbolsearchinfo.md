---
title: "IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs"
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
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Chiamato da un gestore eventi per recuperare i risultati su un processo di caricamento dei simboli.  
  
## Sintassi  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```c#  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### Parametri  
 `pModule`  
 \[out\]  un oggetto IDebugModule3 che rappresenta il modulo per il quale i simboli è stato caricato.  
  
 `pbstrDebugMessage`  
 \[in, out\]  Restituisce una stringa contenente tutti i messaggi di errore dal modulo.  Se non c " è errore, questa stringa conterrà solo il nome del modulo ma non viene mai vuota.  
  
> [!NOTE]
>  \[C\+\+\] `pbstrDebugMessage` non può essere `NULL` e deve essere è stata liberata con `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 \[out\]  Una combinazione di flag [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) dall'enumerazione che indica se i simboli sono stati caricati.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce un codice di errore.  
  
## Note  
 Quando un gestore riceve [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) l'evento dopo viene effettuato un tentativo di caricare i simboli di debug per un modulo, il gestore può chiamare il thismethod per determinare i risultati del caricamento.  
  
## Vedere anche  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)