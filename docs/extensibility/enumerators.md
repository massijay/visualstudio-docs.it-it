---
title: "Enumeratori | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origine plug-in del controllo, gli enumeratori"
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Enumeratori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa sezione sono elencati i tipi di dati di enumeratore nell'API di plug\-in controllo di origine che è necessario conoscere il plug\-in del controllo del codice sorgente.  
  
## In questa sezione  
 [Codice di comando](../extensibility/command-code-enumerator.md)  
 Enumera le opzioni per la [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md) funzioni.  
  
 [Messaggio](../extensibility/message-enumerator.md)  
 Enumera i flag utilizzati per il callback stampa [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Codice di stato file](../extensibility/file-status-code-enumerator.md)  
 Contiene valori costanti denominati che specificano lo stato di un file di controllo del codice sorgente.  
  
 [Codice di stato di directory](../extensibility/directory-status-code-enumerator.md)  
 Contiene valori costanti denominati che specificano lo stato di una directory di controllo del codice sorgente.  
  
## Sezioni correlate  
 [Creazione di plug\-in un controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definisce il SDK di plug\-in controllo di origine e vengono descritte le risorse incluse.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Richiede all'utente per le opzioni avanzate per il comando specificato.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Esamina l'elenco di file per il relativo stato corrente. Inoltre, utilizza il `pfnPopulate` funzione per segnalare al chiamante quando un file non corrispondono ai criteri per il `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Viene descritta la funzione di callback che viene utilizzata da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal controllo di origine del plug\-in tramite l'IDE.  
  
 [Plug\-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)  
 Fornisce un elenco completo di tutti gli elementi nell'API di plug\-in controllo di origine.