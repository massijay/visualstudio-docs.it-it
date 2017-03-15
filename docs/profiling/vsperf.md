---
title: "VSPerf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# VSPerf
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzare lo strumento da riga di comando **VsPerf** per:  
  
1.  Profilare applicazioni di Windows Store dalla riga di comando quando Visual Studio non è installato sul dispositivo.  
  
2.  Profilare applicazioni desktop di Windows 8 e applicazioni Windows Server 2012 utilizzando il metodo di profilatura del campionamento.  
  
 Per ulteriori informazioni sulle opzioni di profilatura, vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 In questo argomento vengono descritte le opzioni che è possibile utilizzare con lo strumento da riga di comando `vsperf.exe`.  In questo argomento sono contenute le sezioni seguenti:  
  
 [solo Applicazioni Windows Store](#BKMK_windows_store_apps_only)  
  
 [solo applicazioni Windows 8 desktop e applicazioni Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Tutte le applicazioni](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> solo Applicazioni Windows Store  
 Queste opzioni sono valide solo per le applicazioni di Windows Store.  
  
|||  
|-|-|  
|**\/app:{AppName}**|Avvia il profiler e attende che l'applicazione specificata venga avviata dal menu Start.<br /><br /> Eseguire `vsperf /listapps` per visualizzare il nome dell'applicazione e il PackageFullName delle applicazioni installate.|  
|**\/package:{PackageFullName}**|Avvia il profiler e attende che l'applicazione specificata venga avviata dal menu Start.<br /><br /> Eseguire `vsperf /listapps` per visualizzare il nome dell'applicazione e il PackageFullName delle applicazioni installate.|  
|**\/js**|Obbligatorio per profilare applicazioni JavaScript.<br /><br /> Raccogliere dati di prestazioni dalle applicazioni JavaScript.<br /><br /> Utilizzare solo con \/package o \/attach.|  
|**\/noclr**|Facoltativa.  Non raccogliere dati CLR.<br /><br /> Utilizzare solo con \/package o \/attach.<br /><br /> Ottimizzazione, i simboli gestiti non vengono risolti.|  
|**\/listapps**|Nomi e PackageFullNames dell'elenco delle applicazione installate.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> solo applicazioni Windows 8 desktop e applicazioni Windows Server 2012  
 Queste opzioni non funzionano con le applicazioni di Windows Store.  
  
|||  
|-|-|  
|**\/launch:{Executable}**|Inizia e avvia la profilatura del file eseguibile dato.|  
|**\/args:{ExecutableArguments}**|Specifica gli argomenti della riga di comando di passare la destinazione di **\/launch**.|  
|**\/console**|Esegue la destinazione di **\/launch** in una nuova finestra di comando.|  
  
##  <a name="BKMK_All_applications"></a> Tutte le applicazioni  
 Queste opzioni si applicano a qualsiasi applicazione di Windows 8 o Windows Server 2012.  
  
|||  
|-|-|  
|**\/attach:{PID&#124;ProcessName}\[,PID&#124;ProcessName\]...**|Raccoglie i dati dai processi specificati.<br /><br /> Utilizzare Gestione attività per visualizzare i nomi dei processi e gli id dei processi \(PID\) delle applicazioni in esecuzione.|  
|**\/file:{ReportName}**|Facoltativa.  Specifica un file di output \(sovrascrive il file esistente\).<br /><br /> Utilizzare solo con \/package o \/attach.|  
|**\/pause**|Sospende la raccolta di dati.|  
|**\/resume**|Riprende la raccolta di dati.|  
|**\/stop**|Arresta la raccolta dati e termina i processi di destinazione.|  
|**\/detach**|Arresta la raccolta dati, ma i processi di destinazione continuano l'esecuzione.|  
|**\/status**|Mostrare lo stato del profiler.|  
  
## Vedere anche  
 [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)