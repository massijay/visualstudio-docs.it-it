---
title: "Profilatura rapida di sito Web con VSPerfASPNETCmd | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per la profilatura, VSPerfASPNETCmd"
  - "VSPerfASPNETCmd"
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Profilatura rapida di sito Web con VSPerfASPNETCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lo strumento da riga di comando **VSPerfASPNETCmd** consente di profilare facilmente applicazioni Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Rispetto allo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md), le opzioni sono ridotte, non è necessario impostare variabili di ambiente e non è richiesto il riavvio del computer.  **VSPerfASPNETCmd** è il metodo preferito per profilare tramite il profiler autonomo.  Per ulteriori informazioni, vedere [Procedura: installare il profiler autonomo](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
>  Le funzioni di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio.  Le applicazioni Windows Store richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 In alcuni scenari, ad esempio la raccolta di dati di concorrenza o la sospensione e ripresa della profilatura tramite **VSPerfCmd**, costituisce il metodo di profilatura preferito.  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Su computer a 64 bit utilizzare lo strumento VSPerfASPNETCmd disponibile nella directory 32 bit\\Team Tools\\Performance Tools.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Profilatura di un'applicazione ASP.NET  
 Per profilare un'applicazione Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], digitare uno dei comandi descritti nelle sezioni seguenti.  Il sito Web viene avviato e il profiler inizia a raccogliere dati.  Verificare la funzionalità dell'applicazione, quindi chiudere il browser.  Per interrompere la profilatura, premere INVIO nella finestra del prompt dei comandi.  
  
> [!NOTE]
>  Per impostazione predefinita, il prompt dei comandi non viene ripristinato dopo l'esecuzione del comando **vsperfaspnetcmd**.  È possibile utilizzare l'opzione **\/nowait** per imporre il ripristino del prompt dei comandi.  Vedere [Utilizzo dell'opzione /NoWait](#UsingNoWait).  
  
## Per raccogliere statistiche sull'applicazione utilizzando il metodo di campionamento  
 Il campionamento è il metodo di profilatura predefinito dello strumento **VSPerfASPNETCmd** e non è necessario specificarlo nella riga di comando.  La riga di comando seguente consente di raccogliere statistiche dell'applicazione dall'applicazione Web specificata:  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## Per raccogliere dati di intervallo dettagliati tramite il metodo di strumentazione  
 Utilizzare la riga di comando seguente per raccogliere dati di intervallo dettagliati da un'applicazione Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilata dinamicamente:  
  
 **vsperfaspnetcmd \/trace**  *websiteUrl*  
  
 Se si desidera profilare file DLL compilati staticamente nell'applicazione Web, è necessario a instrumentare i file tramite lo strumento da riga di comando [VSInstr](../profiling/vsinstr.md).  Il comando vsperfaspnetcmd \/trace includerà dati dai file instrumentati.  
  
## Per raccogliere dati di memoria .NET  
 L'opzione **\/Memory** consente di raccogliere dati sull'allocazione di oggetti nella memoria .NET ed è in grado di raccogliere dati sulla durata di tali oggetti.  La raccolta di dati di allocazione è la modalità predefinita dell'opzione **\/Memory** e non è necessario specificarla nella riga di comando.  
  
 **vsperfaspnetcmd \/memory** *websiteUrl*  
  
 Utilizzare il parametro **Lifetime** per raccogliere dati di durata dell'oggetto oltre ai dati di allocazione:  
  
 **vsperfaspnetcmd \/memory:lifetime** *websiteUrl*  
  
 È inoltre possibile utilizzare l'opzione **\/Trace** per includere informazioni dettagliate sull'intervallo con i dati di memoria .NET:  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/trace** `websiteUrl`  
  
## Per raccogliere dati di interazione tra livelli  
  
> [!WARNING]
>  I dati di profilatura dell'interazione tra livelli \(TIP\) possono essere raccolti utilizzando [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], o [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)].  Tuttavia, i dati della profilatura dell'interazione tra livelli possono essere visualizzati solo in [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] e in [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
>   
>  Per raccogliere dati TIP in Windows 8 o Windows Server 2012, è necessario utilizzare l'opzione di strumentazione \(**\/trace**\).  
  
 Per raccogliere dati di interazione tra livelli con dati di campionamento:  
  
 **vsperfaspnetcmd \/tip** `websiteUrl`  
  
 Per raccogliere dati di interazione tra livelli con dati di strumentazione:  
  
 **vsperfaspnetcmd \/trace \/tip** *websiteUrl*  
  
 Per raccogliere dati di interazione tra livelli con dati di memoria .NET:  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/tip** *websiteUrl*  
  
##  <a name="UsingNoWait"></a> Utilizzo dell'opzione \/NoWait  
 Per impostazione predefinita, il prompt dei comandi non viene ripristinato dopo l'esecuzione del comando **vsperfaspnetcmd**.  È possibile utilizzare l'opzione della sintassi seguente per imporre il ripristino del prompt dei comandi.  Sarà quindi possibile eseguire altre operazioni nella finestra del prompt dei comandi.  Per terminare la profilatura, utilizzare l'opzione **\/shutdown** in un comando **vsperfaspnetcmd** separato.  
  
 Per iniziare la profilatura:  
  
 **vsperfaspnetcmd** \[*\/Options*\] **\/nowait** *websiteUrl*  
  
 Per terminare la profilatura:  
  
 **vsperfaspnetcmd \/shutdown** *websiteUrl*  
  
## Opzioni aggiuntive  
 È possibile aggiungere una qualsiasi delle opzioni seguenti ai comandi elencati precedentemente in questa sezione, tranne il comando **vsperfaspnetcmd \/shutdown**.  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**\/Output:** `VspFile`|Per impostazione predefinita, il file dei dati di profilatura \(con estensione vsp\) viene creato nella directory corrente con nome file **PerformanceReport.vsp**.  Utilizzare l'opzione \/output per specificare un percorso o nome file diverso o entrambi.|  
|**\/PackSymbols:Off**|Per impostazione predefinita, VsPerfASPNETCmd incorpora simboli, ovvero nomi di funzione e di parametro e così via, nel file con estensione vsp.  L'incorporamento di simboli può aumentare considerevolmente le dimensioni del file dei dati di profilatura.  Se si prevede di disporre dell'accesso ai file con estensione pdb contenenti i simboli quando si analizzano i dati, utilizzare l'opzione \/packsymbols:off per disabilitare l'incorporamento dei simboli.|