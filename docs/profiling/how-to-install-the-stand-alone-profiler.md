---
title: "Procedura: installare il profiler autonomo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti di prestazioni, installazione del profiler autonomo"
  - "strumenti di profilatura, profiler autonomo"
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Procedura: installare il profiler autonomo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornisce una riga di comando basata su un profiler autonomo che può essere eseguito senza installare l’IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Questa situazione si verifica quando un computer non dispone o non può disporre di un ambiente di sviluppo installato.  Ad esempio, non è necessario installare un ambiente di sviluppo su un server Web di produzione.  
  
> [!NOTE]
>  Quando si utilizza il profiler autonomo per raccogliere dati di prestazioni per il sito Web ASP.NET, è preferibile utilizzare lo strumento da riga di comando [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) anziché lo strumento [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### Installare il profiler autonomo  
  
1.  Individuare il programma di installazione del profilo autonomo \(vs\_profiler.exe\) sul supporto di installazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nella directory che include il percorso \\Standalone Profile ed eseguirlo.  
  
2.  Aggiungere i percorsi vsintr.exe e msdis150.dll al percorso di sistema.  
  
    > [!NOTE]
    >  Nell'installazione predefinita di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vsinstr.exe e msdis150.dll si trovano nel percorso \\Programmi\\Visual Studio 10\\Team Tools\\Performance Tools.  
  
3.  Al prompt dei comandi digitare **VSInstr**.  
  
    > [!NOTE]
    >  Se vengono visualizzate le informazioni di utilizzo per vsinstr.exe, tutto è impostato correttamente.  Se viene visualizzato un errore che indica che vsinstr.exe o una delle dipendenze non è stata trovata, assicurarsi di aver inserito correttamente i percorsi come descritto nel passaggio 2.  
  
4.  Configurare il server di simboli impostando la variabile **\_NT\_SYMBOL\_PATH** su **symsrv\*symsrv.dll\*c:\\localcache\*http:\/\/msdl.microsoft.com\/download\/symbols**  
  
5.  Dopo avere impostato il server di simboli utilizzando le variabili dell'ambiente di sistema, eseguire gli strumenti della riga di comando del profiler ad un nuovo prompt dei comandi.  Consente alle nuove variabili dell’ambiente di essere applicate.  Nella finestra del prompt dei comandi digitare il comando seguente:  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  Per istruzioni dettagliate sulla configurazione del pacchetto del server di simboli, vedere [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Utilizzare lo strumento [VSPerfReport](../profiling/vsperfreport.md) per serializzare i simboli nel file di di dati di analisi \(vsp\).  Utilizzare le opzioni **VSPerfReport \/summary:all \/packsymbols**.  Se nel file di dati non sono presenti simboli, assicurarsi che sia impostata la variabile di ambiente \_NT\_SYMBOL\_PATH.  
  
## Vedere anche  
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Procedura dettagliata: Profilatura dalla riga di comando tramite campionamento](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Procedura dettagliata: Profilatura dalla riga di comando tramite strumentazione](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)