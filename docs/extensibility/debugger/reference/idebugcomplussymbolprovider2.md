---
title: "IDebugComPlusSymbolProvider2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugComPlusSymbolProvider2"
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugComPlusSymbolProvider2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Rappresenta un provider del simbolo COM\+ con i metodi specifici del codice gestito ed estende **il IDebugComPlusSymbolProvider[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)**.  
  
## Sintassi  
  
```  
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider  
```  
  
## Metodi  
 Oltre ai metodi [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) in un'interfaccia, l'interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[FunctionHasLineInfo](../Topic/IDebugComPlusSymbolProvider2::FunctionHasLineInfo.md)|Determina se il metodo specificato contiene informazioni sulla riga.|  
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Recupera un tipo in base al nome.|  
|[GetTypeFromToken](../Topic/IDebugComPlusSymbolProvider2::GetTypeFromToken.md)|Recupera un tipo fornito il relativo token.|  
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|determina se l'indirizzo specificato di debug è un punto di sequenza.|  
|[LoadSymbolsFromCallback](../Topic/IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback.md)|Carica simboli di debug utilizzando il metodo di callback specificato.|  
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|I simboli di debug del caricamento da un flusso di dati fornito **il ICorDebugModule** oggetto.|  
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|Simboli di debug carichi forniti l'oggetto **di ICorDebugModule** .|  
  
## Requisiti  
 intestazione: Sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll