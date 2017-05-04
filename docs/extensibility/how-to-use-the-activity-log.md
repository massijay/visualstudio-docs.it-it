---
title: "Procedura: utilizzare il registro attività | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c9df048a49580f3526b48e29041ef3758722ed27
ms.openlocfilehash: dc821f22a04432989a2edb68c483d298ffcf0eb7
ms.lasthandoff: 05/03/2017

---
# <a name="how-to-use-the-activity-log"></a>Procedura: utilizzare il registro attività
Pacchetti VSPackage possono scrivere messaggi nel registro attività. Questa funzionalità è particolarmente utile per il debug di pacchetti VSPackage in ambienti di vendita al dettaglio.  
  
> [!TIP]
>  Il registro attività è sempre attivato. Visual Studio consente di mantenere un buffer in sequenza delle voci di ultima cento, nonché le prime dieci voci, le informazioni di configurazione generale.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Per scrivere una voce nel log attività  
  
1.  Inserire questo codice nel metodo < xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A > o in qualsiasi altro metodo tranne che nel costruttore VSPackage:  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Questo codice ottiene il servizio < xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog > e ne esegue il cast a un'interfaccia < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog >. < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A > scrive una voce informativo nel log delle attività utilizzando il contesto relative alla lingua corrente.  
  
2.  Quando il pacchetto VSPackage è caricato (in genere quando viene richiamato un comando o si apre una finestra), il testo venga scritto nel registro attività.  
  
### <a name="to-examine-the-activity-log"></a>Per esaminare il registro attività  
  
1.  Trovare il log attività nella sottocartella per i dati di Visual Studio: *% AppData %*\Microsoft\VisualStudio\15.0\ActivityLog.XML...  
  
2.  Aprire il registro attività con qualsiasi editor di testo. Di seguito è una voce tipici:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Poiché il registro attività è un servizio, il registro attività non è disponibile nel costruttore VSPackage.  
  
 È necessario ottenere il registro attività appena prima di scrivere in esso. Non memorizzare nella cache o salvare il registro attività per un utilizzo futuro.  
  
## <a name="see-also"></a>Vedere anche  
 < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog >   
 < xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE >   
 [Risoluzione dei problemi di VSPackage](../extensibility/troubleshooting-vspackages.md)   
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)

