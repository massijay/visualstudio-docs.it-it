---
title: "Funzioni di callback implementate dall&#39;IDE | Microsoft Docs"
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
  - "origine plug-in del controllo, le funzioni di callback"
  - "funzioni di callback, plug-in del controllo codice sorgente"
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzioni di callback implementate dall&#39;IDE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Affinché l'integrazione con l'ambiente di sviluppo integrato \(IDE\) come trasparente possibile e per fornire un'esperienza unificata per l'utente finale, il plug\-in del controllo del codice sorgente può utilizzare funzioni di callback che vengono implementate dall'IDE. Il plug\-in può chiamare queste funzioni in momenti appropriati durante un'operazione di controllo di origine per passare informazioni a IDE; l'IDE può quindi visualizzare queste informazioni come elementi incorporati nella relativa interfaccia utente nativa. L'utente ha un'esperienza meno frammentata in questo scenario rispetto a se il plug\-in utilizzati la propria interfaccia utente.  
  
 Il file di intestazione obbligatoria è scc.h. Il percorso predefinito è \\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc\\. È anche nella cartella VSIP che possiede l'esempio di plug\-in del controllo di origine in \\Program Files\\VSIP 8.0\\MSSCCI\\.  
  
## In questa sezione  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Viene descritta la funzione di callback che viene utilizzata da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal controllo di origine del plug\-in tramite l'IDE.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Viene descritta la funzione di callback che viene utilizzata da [SccPopulateList](../extensibility/sccpopulatelist-function.md) quando l'IDE non dispone di accesso completo alle informazioni che sono disponibile solo per il controllo del codice sorgente del plug\-in, ad esempio un elenco completo dei file nel controllo della versione.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Viene descritta la funzione di callback che viene utilizzata il [SccQueryChanges](../extensibility/sccquerychanges-function.md) operazione.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Viene descritta la funzione di callback che viene utilizzata il [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operazione.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Viene descritta la funzione di callback impostata da una chiamata per il [SccSetOption](../extensibility/sccsetoption-function.md) che consente il controllo del codice sorgente del plug\-in per comunicare modifiche di nome all'IDE.  
  
## Sezioni correlate  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Apre un progetto.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Esamina l'elenco di file per il relativo stato corrente. Inoltre, utilizza il `pfnPopulate` funzione per segnalare al chiamante quando un file non corrispondono ai criteri per il `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Esamina un elenco di directory e file in un progetto o progetti inclusi nel controllo del codice sorgente. Ogni nome di file e directory trovato viene passato a una funzione di callback.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Esamina modifiche ai nomi che sono state apportate a un elenco di file. Ogni nome di file viene passato a una funzione di callback assieme al suo stato di modifica.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Imposta un'ampia gamma di opzioni. Ogni opzione inizia con `SCC_OPT_xxx` e ha un proprio insieme di valori definiti.  
  
 [Plug\-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)  
 Viene descritto il contenuto della sezione di riferimento del SDK di plug\-in controllo di origine.