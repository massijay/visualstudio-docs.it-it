---
title: "Procedura: utilizzare il registro attivit&#224; | Microsoft Docs"
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
  - "Package VS, debug"
  - "Package VS, risoluzione dei problemi"
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: utilizzare il registro attivit&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Package VS può scrivere messaggi nel registro attività. Questa funzionalità è particolarmente utile per il debug di VSPackage in ambienti di vendita al dettaglio.  
  
> [!TIP]
>  Il registro attività è sempre attivato. Visual Studio mantiene un buffer in sequenza le voci di cento ultima che le prime dieci voci, le informazioni di configurazione generale.  
  
### Per scrivere una voce nel log attività  
  
1.  Inserire il codice di <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo o in qualsiasi altro metodo, ad eccezione del costruttore VSPackage:  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Questo codice ottiene il <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> del servizio e ne esegue il cast a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaccia.<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Scrive una voce informativo nel log delle attività utilizzando il contesto relative alla lingua corrente.  
  
2.  Quando viene caricato il VSPackage \(in genere, quando viene richiamato un comando o si apre una finestra\), il testo viene scritto nel registro attività.  
  
### Per esaminare il registro attività  
  
1.  Trovare il registro attività nella sottocartella per i dati di Visual Studio: *% AppData %*\\Microsoft\\VisualStudio\\14.0\\ActivityLog.XML...  
  
2.  Aprire il registro attività con qualsiasi editor di testo. Di seguito è una voce tipica:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## Programmazione efficiente  
 Poiché il registro attività è un servizio, il registro attività non è disponibile nel costruttore VSPackage.  
  
 È necessario ottenere il registro attività appena prima della scrittura a esso. Non memorizzare nella cache o salvare il registro attività per un utilizzo futuro.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Risoluzione dei problemi di VSPackage](../extensibility/troubleshooting-vspackages.md)   
 [Package VS](../extensibility/internals/vspackages.md)