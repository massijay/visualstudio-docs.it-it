---
title: "Writing Multi-Processor-Aware Loggers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, multi-proc aware loggers"
  - "multi-proc loggers"
  - "loggers, multi-proc"
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Writing Multi-Processor-Aware Loggers
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La possibilità di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di sfruttare più processori può ridurre i tempi di compilazione del progetto, ma aggiunge complessità alla registrazione dell'evento di compilazione.  In un ambiente a processore singolo, eventi, messaggi, avvisi ed errori arrivano al logger in modo prevedibile e sequenziale.  In un ambiente multiprocessore, eventi di origini diverse possono verificarsi contemporaneamente o fuori sequenza.  A tale scopo, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornisce un logger compatibile con più processori e un nuovo modello di registrazione e consente di creare "logger di inoltro" personalizzati.  
  
## Problematiche relative alla registrazione a più processori  
 Quando si compila uno o più progetti su un sistema a più processori o a più componenti principali, gli eventi di compilazione di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per tutti i progetti vengono generati contemporaneamente.  Il logger può ricevere una notevole quantità di messaggi di evento contemporaneamente o fuori sequenza.  Poiché un logger [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 non è concepito per gestire tali situazioni, è possibile che il logger venga sovraccaricato e i tempi di compilazione aumentino, che l'output del logger non sia corretto o che la compilazione venga interrotta.  Per affrontare tali problemi, il logger \(a partire da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5\) può elaborare eventi fuori sequenza ed eventi correlati e le relative origini.  
  
 È possibile migliorare ulteriormente l'efficienza della registrazione creando un logger di inoltro personalizzato.  Un logger di inoltro personalizzato agisce come un filtro consentendo di scegliere, prima della compilazione, solo gli eventi che si desidera controllare.  Quando si utilizza un logger di inoltro personalizzato, gli eventi indesiderati non possono sovraccaricare il logger, ingombrare i log, o rallentare i tempi di compilazione.  
  
## Modelli di registrazione a più processori  
 Per affrontare i problemi di compilazione correlati a più processori, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] supporta due modelli di registrazione, centrale e distribuito.  
  
### Modello di registrazione centrale  
 Nel modello di registrazione centrale, una sola istanza di MSBuild.exe agisce come "nodo centrale" e le istanze figlio del nodo centrale \("nodi secondari"\) si associano al nodo centrale per agevolare le attività di compilazione.  
  
 ![Modello di logger centrale](../msbuild/media/centralnode.png "CentralNode")  
  
 I logger di diversi tipi associati al nodo centrale sono noti come "logger centrali". È possibile associare solo un'istanza di ciascun tipo di logger al nodo centrale contemporaneamente.  
  
 Quando si verifica una compilazione, i nodi secondari indirizzano gli eventi di compilazione al nodo centrale.  Il nodo centrale indirizza tutti gli eventi, anche quelli dei nodi secondari, a uno o più dei logger centrali associati.  I logger creano quindi file di log basati sui dati in ingresso.  
  
 Anche se è richiesta l'implementazione solo di <xref:Microsoft.Build.Framework.ILogger> da parte del logger centrale, è consigliabile implementare anche <xref:Microsoft.Build.Framework.INodeLogger> in modo che il logger centrale venga inizializzato con il numero di nodi parte della compilazione.  L'overload seguente del metodo <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> viene richiamato quando il motore inizializza il logger.  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
 Qualsiasi logger preesistente basato su <xref:Microsoft.Build.Framework.ILogger> è in grado di agire da logger centrale e di associarsi alla compilazione.  Tuttavia, logger centrali scritti senza supporto esplicito per scenari di registrazione a più processori ed eventi non in ordine possono interrompere una compilazione o possono produrre output non significativo.  
  
### Modello di registrazione distribuito  
 Nel modello di registrazione centrale, il traffico in eccesso dei messaggi in ingresso può sovraccaricare il nodo centrale, ad esempio, in caso di compilazione di più progetti contemporaneamente.  Le risorse di sistema possono essere sottoposte a stress eccessivo e le prestazioni di compilazione ridursi.  Per alleviare questo problema [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] supporta un modello di registrazione distribuito.  
  
 ![Modello di registrazione distribuita](../msbuild/media/distnode.png "DistNode")  
  
 Il modello di registrazione distribuito estende il modello di registrazione centrale consentendo di creare un logger di inoltro.  
  
#### Logger di inoltro  
 Un logger di inoltro è un logger secondario, leggero che dispone di un filtro eventi associato a un nodo secondario e che riceve eventi di compilazione in ingresso da tale nodo.  Filtra gli eventi in ingresso e inoltra solo quelli specificati al nodo centrale.  In tal modo il traffico dei messaggi inviati al nodo centrale risulta ridotto e in generale le prestazioni di compilazione migliorano.  
  
 Sono disponibili due modalità per utilizzare la registrazione distribuita, come segue:  
  
-   Personalizzare il logger di inoltro preimpostato denominato <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>.  
  
-   Scrivere logger di inoltro personalizzato.  
  
 È possibile modificare ConfigurableForwardingLogger per adattarlo ai requisiti.  A tale scopo, chiamare il logger dalla riga di comando utilizzando MSBuild.exe ed elencare gli eventi di compilazione che si desidera vengano inoltrati dal logger al nodo centrale.  
  
 In alternativa, è possibile creare un logger di inoltro personalizzato.  Creando un logger di inoltro personalizzato, è possibile ottimizzare il comportamento del logger.  La creazione di un logger di inoltro personalizzato è tuttavia più complessa della personalizzazione del solo ConfigurableForwardingLogger.  Per ulteriori informazioni, vedere [Creating Forwarding Loggers](../msbuild/creating-forwarding-loggers.md).  
  
## Utilizzo di ConfigurableForwardingLogger per la registrazione distribuita semplice  
 Per associare un ConfigurableForwardingLogger o un logger di inoltro personalizzato, utilizzare l'opzione `/distributedlogger` \(`/dl` in breve\) in una compilazione da riga di comando di MSBuild.exe.  Il formato per la specifica dei nomi dei tipi di logger e delle classi è lo stesso di quello per l'opzione `/logger`, ma un logger distribuito presenta sempre due classi di registrazione anziché una: il logger di inoltro e il logger centrale.  Di seguito è riportato un esempio di come associare un logger di inoltro personalizzato denominato XMLForwardingLogger.  
  
```  
msbuild.exe myproj.proj/distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral  
```  
  
> [!NOTE]
>  I due nomi dei logger nell'opzione `/dl` devono essere separati da un asterisco \(\*\).  
  
 L'utilizzo di ConfigurableForwardingLogger è simile all'utilizzo di qualsiasi altro logger \(come accennato in [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)\), con l'eccezione che si associa il logger di ConfigurableForwardingLogger anziché il logger [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tipico e si specificano come parametri gli eventi che devono essere passati al nodo centrale da parte di ConfigurableForwardingLogger.  
  
 Ad esempio, se si desidera ricevere notifica solo all'inizio e al termine di una compilazione e quando si verifica un errore, si passano `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT` e `ERROREVENT` come parametri.  È possibile passare più parametri separandoli con un punto e virgola.  Di seguito è riportato un esempio di come utilizzare ConfigurableForwardingLogger per inoltrare solo gli eventi `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT` e `ERROREVENT`.  
  
```  
msbuild.exe myproj.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT  
```  
  
 Di seguito viene riportato un elenco dei parametri ConfigurableForwardingLogger disponibili.  
  
|Parametri ConfigurableForwardingLogger|  
|--------------------------------------------|  
|BUILDSTARTEDEVENT|  
|BUILDFINISHEDEVENT|  
|PROJECTSTARTEDEVENT|  
|PROJECTFINISHEDEVENT|  
|TARGETSTARTEDEVENT|  
|TARGETFINISHEDEVENT|  
|TASKSTARTEDEVENT|  
|TASKFINISHEDEVENT|  
|ERROREVENT|  
|WARNINGEVENT|  
|HIGHMESSAGEEVENT|  
|NORMALMESSAGEEVENT|  
|LOWMESSAGEEVENT|  
|CUSTOMEVENT|  
|COMMANDLINE|  
|PERFORMANCESUMMARY|  
|NOSUMMARY|  
|SHOWCOMMANDLINE|  
  
## Vedere anche  
 [Creating Forwarding Loggers](../msbuild/creating-forwarding-loggers.md)