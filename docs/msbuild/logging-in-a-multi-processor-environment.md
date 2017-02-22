---
title: "Logging in a Multi-Processor Environment | Microsoft Docs"
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
  - "MSBuild, multi-processor logging"
  - "MSBuild, logging"
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Logging in a Multi-Processor Environment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La capacità di MSBuild di utilizzare più processori può ridurre notevolmente i tempi di compilazione del progetto, ma aggiunge complessità alla registrazione.  In un ambiente a processore singolo, il logger è in grado di gestire eventi, messaggi, avvisi ed errori in ingresso in modo prevedibile e sequenziale.  In un ambiente multiprocessore, invece, eventi di origini diverse possono verificarsi contemporaneamente o fuori sequenza.  MSBuild fornisce un nuovo logger compatibile con più processori e consente la creazione di "logger di inoltro" personalizzati.  
  
## Registrazione di compilazioni a più processori  
 Quando si compila uno o più progetti in un sistema a più processori o a più core, MSBuild compila gli eventi contemporaneamente per tutti i progetti che vengono generati.  Il logger può ricevere una notevole quantità di dati di evento contemporaneamente o fuori sequenza.  Ciò può sovraccaricare il logger e causare un aumento dei tempi di compilazione, un output non corretto del logger, o persino interrompere la compilazione.  Per affrontare tali problemi, il logger di MSBuild può elaborare eventi fuori sequenza e correlare gli eventi e le loro fonti.  
  
 È possibile migliorare ulteriormente l'efficienza della registrazione creando un logger di inoltro personalizzato.  Un logger di inoltro personalizzato agisce come un filtro consentendo di scegliere, prima della compilazione, gli eventi che si desidera controllare.  Quando si utilizza un logger di inoltro personalizzato, gli eventi indesiderati non possono sovraccaricare il logger, ingombrare i log, o rallentare i tempi di compilazione.  
  
### Modello di registrazione centrale  
 Per le compilazioni a più processori, MSBuild utilizza un "modello di registrazione centrale". Nel modello di registrazione centrale, un'istanza di MSBuild.exe agisce come processo di compilazione primario, o "nodo centrale". Le istanze secondarie di MSBuild.exe, o "nodi secondari", sono associate al nodo centrale.  I logger basati su ILogger e associati al nodo centrale sono noti come "logger centrali" e i logger associati ai nodi secondari sono noti come "logger secondari".  
  
 Quando si verifica una compilazione, i logger secondari indirizzano il traffico eventi ai logger centrali.  Poiché gli eventi originano molti nodi secondari, i dati arrivano simultaneamente al nodo centrale ma con interfoliazione.  Per risolvere i riferimenti tra evento e progetti e tra evento e destinazione, gli argomenti dell'evento includono informazioni di contesto aggiuntive sugli eventi di compilazione.  
  
 Anche se è richiesta l'implementazione solo di <xref:Microsoft.Build.Framework.ILogger> da parte del logger centrale, è consigliabile implementare anche <xref:Microsoft.Build.Framework.INodeLogger> in modo che il logger centrale venga inizializzato con il numero di nodi parte della compilazione.  L'overload seguente del metodo <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> viene richiamato quando il motore inizializza il logger.  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### Modello di registrazione distribuito  
 Nel modello di registrazione centrale, il traffico in eccesso dei messaggi in ingresso può sovraccaricare il nodo centrale, ad esempio, in caso di compilazione di più progetti contemporaneamente. Il sistema può risultare sovraccarico e le prestazioni di compilazione ridotte.  
  
 Per ridurre il problema, MSBuild offre anche un "modello di registrazione distribuito" che estende il modello di registrazione centrale consentendo di creare logger di inoltro.  Un logger di inoltro viene associato a un nodo secondario e riceve eventi di compilazione in ingresso da tale nodo.  Il logger di inoltro è simile a un logger normale salvo che può filtrare gli eventi e quindi inoltrare al nodo centrale solo quelli desiderati.  Il traffico di messaggi al nodo centrale risulta ridotto e pertanto le prestazioni sono migliori.  
  
 È possibile creare un logger di inoltro implementando l'interfaccia <xref:Microsoft.Build.Framework.IForwardingLogger> che deriva da <xref:Microsoft.Build.Framework.ILogger>.  L'interfaccia viene definita come segue:  
  
```  
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 Per inoltrare gli eventi in un logger di inoltro, chiamare il metodo <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> dell'interfaccia <xref:Microsoft.Build.Framework.IEventRedirector>.  Come parametro, passare l'oggetto <xref:Microsoft.Build.Framework.BuildEventArgs> appropriato, o un derivato.  
  
 Per ulteriori informazioni, vedere [Creating Forwarding Loggers](../msbuild/creating-forwarding-loggers.md).  
  
### Associazione di un logger distribuito  
 Per associare un logger distribuito su una compilazione da riga di comando, utilizzare l'opzione `/distributedlogger` \(o `/dl` in breve\).  Il formato per la specifica dei nomi dei tipi di logger e delle classi è lo stesso di quello per l'opzione `/logger`, ma un logger distribuito presenta due classi di registrazione: un logger di inoltro e un logger centrale.  Di seguito è riportato un esempio di associazione di un logger distribuito:  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 I due nomi dei logger nell'opzione `/dl` sono separati da un asterisco \(\*\).  
  
## Vedere anche  
 [Build Loggers](../msbuild/build-loggers.md)   
 [Creating Forwarding Loggers](../msbuild/creating-forwarding-loggers.md)