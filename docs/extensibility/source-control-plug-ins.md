---
title: "Plug-in del controllo codice sorgente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origine plug-in del controllo, riferimento"
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Plug-in del controllo codice sorgente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La sezione di riferimento SDK plug\-in controllo di origine contiene la specifica di interfaccia completa che consente ai sistemi di controllo di origine per l'integrazione con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Specifica la sintassi e semantica i vari tipi di dati e funzioni che il plug\-in del controllo del codice sorgente deve implementare per l'interazione con il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato \(IDE\).  
  
## In questa sezione  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)  
 Elenca le funzioni che devono essere implementate per il plug\-in del controllo del codice sorgente per garantire la conformità con l'API plug\-in controllo di origine.  
  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Vengono descritte le funzioni che il plug\-in del controllo del codice sorgente utilizzato per passare informazioni tornare all'IDE, mentre alcuni comandi vengono eseguiti.  
  
 [Enumeratori](../extensibility/enumerators.md)  
 Elenca i tipi di dati di enumeratore nell'API di plug\-in controllo di origine che è necessario conoscere il plug\-in del controllo del codice sorgente.  
  
 [Flag di capacità](../extensibility/capability-flags.md)  
 Viene descritto il `SCC_CAP_xxx` flag, che sono indicato le funzionalità del provider.  
  
 [Flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)  
 Elenca i flag che sono utili nel contesto di comandi specifici.  
  
 [Codici di errore](../extensibility/error-codes.md)  
 Vengono elencati i valori di errore comuni restituiti dalle funzioni come `SCCTRN`.  
  
 [Stringhe utilizzate come chiavi per la ricerca di un controllo del codice sorgente del plug\-in](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Vengono descritte le chiavi per l'accesso del Registro di sistema per individuare il controllo del codice sorgente plug\-in.  
  
 [MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md)  
 Descrive un file lato client che contiene informazioni opache all'IDE, ma che viene utilizzato il plug\-in del controllo del codice sorgente per individuare la soluzione o progetto nel controllo della versione.  
  
 [Procedure consigliate per implementare un plug\-in del controllo del codice sorgente](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Fornisce una raccolta di promemoria tecniche importanti da ricordare quando si implementa l'API plug\-in controllo di origine.  
  
 [Limitazioni sulle lunghezze di stringa](../extensibility/restrictions-on-string-lengths.md)  
 Vengono descritte le lunghezze delle stringhe utilizzate in varie funzioni limitazioni nell'API di plug\-in controllo di origine.  
  
 [Glossario](../extensibility/source-control-plug-in-glossary.md)  
 Fornisce utili termini e le relative definizioni per leggere la documentazione SDK di plug\-in controllo di origine.  
  
 [Procedura: disabilitare gli avvisi di compatibilità per Plug\-in del controllo codice sorgente](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Viene descritto come disabilitare gli avvisi.  
  
## Sezioni correlate  
 [Source Control Plug\-in Sample](http://msdn.microsoft.com/it-it/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Viene fornito un esempio di plug\-in del controllo del codice sorgente.  
  
 [Guida per i test per il Plug\-in di controllo codice sorgente](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Vengono descritte le procedure di test correlate a un plug\-in del controllo del codice sorgente.  
  
 [Creazione di plug\-in un controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Viene illustrato come creare un controllo del codice sorgente del plug\-in che fornisce controllo del codice sorgente quando si utilizza il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfaccia utente di controllo codice sorgente \(UI\).  
  
 [Riferimento al SDK di Visual Studio](../extensibility/visual-studio-sdk-reference.md)  
 Visualizza un elenco di argomenti di riferimento.