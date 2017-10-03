---
title: Registrazione in un ambiente multiprocessore | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: e78d6c35fa294d2f1a39c91af5e278e9e4519d2d
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="logging-in-a-multi-processor-environment"></a>Registrazione in un ambiente a più processori
La possibilità di MSBuild di utilizzare più processori può ridurre notevolmente i tempi di compilazione del progetto, ma aggiunge complessità alla registrazione. In un ambiente a processore singolo, il logger può gestire gli eventi in ingresso, messaggi, avvisi ed errori in modo prevedibile e sequenza. In un ambiente multiprocessore, tuttavia, gli eventi da diverse origini possono arrivare contemporaneamente o fuori sequenza. MSBuild fornisce un nuovo logger compatibile con più processori e consente di creare "logger di inoltro personalizzati."  
  
## <a name="logging-multiple-processor-builds"></a>Compila la registrazione di più processori  
 Quando si compilano uno o più progetti in un sistema a più processori o multicore, gli eventi di compilazione di MSBuild per tutti i progetti vengono generati contemporaneamente. Una grande quantità di dati dell'evento potrebbero arrivare al logger contemporaneamente o fuori sequenza. Questo può sovraccaricare il logger e causare tempi di compilazione aumentino, output del logger non corretto o compilazione non funzionante. Per risolvere questi problemi, il logger di MSBuild è possibile elaborare gli eventi fuori sequenza e correlare gli eventi e le relative origini.  
  
 È possibile migliorare ulteriormente creando un logger di inoltro personalizzato l'efficienza di registrazione. Un logger di inoltro personalizzato funge da filtro in quanto consente di scegliere, prima della compilazione, gli eventi che si desidera monitorare. Quando si utilizza un logger di inoltro personalizzato, gli eventi indesiderati non sovraccaricare il logger, ingombrare i log o rallentare i tempi di compilazione.  
  
### <a name="central-logging-model"></a>Modello di registrazione centrale  
 Per le compilazioni multiprocessore, MSBuild Usa "modello di registrazione centrale". Nel modello di registrazione centrale, un'istanza di MSBuild.exe agisce come il processo di compilazione primaria, o "nodo centrale". Le istanze secondarie di MSBuild.exe o "nodi secondari", vengono collegate al nodo centrale. Tutti i logger basati su ILogger associati al nodo centrale sono noti come "logger centrale" e i logger associati ai nodi secondari sono note come "logger secondario".  
  
 Quando si verifica una compilazione, il logger secondari indirizzano il traffico eventi per il logger centrale. Poiché gli eventi hanno origine in più nodi secondari, arrivano al nodo centrale contemporaneamente i dati ma con interfoliazione. Per risolvere i riferimenti al progetto di eventi e di destinazione di eventi, gli argomenti dell'evento includono informazioni sul contesto di eventi di compilazione aggiuntive.  
  
 Anche se solo <xref:Microsoft.Build.Framework.ILogger> è richiesta l'implementazione da parte del logger centrale, è consigliabile implementare anche <xref:Microsoft.Build.Framework.INodeLogger> se si desidera che il logger centrale venga inizializzato con il numero di nodi che fanno parte della compilazione. L'overload seguente del <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> metodo viene richiamato quando il motore inizializza il logger:  
  
```csharp
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### <a name="distributed-logging-model"></a>Modello di registrazione distribuita  
 Nel modello di registrazione centrale, una quantità eccessiva traffico di messaggi in ingresso, ad esempio quando compilazione di più progetti in una sola volta, può sovraccaricare il nodo centrale, che un aumento delle dimensioni del sistema e si ridotta le prestazioni di compilazione.  
  
 Per ridurre questo problema, MSBuild offre anche un "modello di registrazione distribuito" che consente di estendere il modello di registrazione centrale consentendo la creazione di logger di inoltro. Un logger di inoltro è collegato a un nodo secondario e riceve eventi di compilazione in ingresso da tale nodo. Il logger di inoltro è analogo a un logger normale ad eccezione del fatto che sia possibile filtrare gli eventi e quindi inoltrare solo quelli desiderati per il nodo centrale. Ciò riduce il traffico dei messaggi in corrispondenza del nodo centrale e consente pertanto prestazioni migliori.  
  
 È possibile creare un logger di inoltro mediante l'implementazione di <xref:Microsoft.Build.Framework.IForwardingLogger> interfaccia, che deriva da <xref:Microsoft.Build.Framework.ILogger>. L'interfaccia è definita come segue:  
  
```csharp
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 Per inoltrare gli eventi in un logger di inoltro, chiamare il <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> metodo il <xref:Microsoft.Build.Framework.IEventRedirector> interfaccia. Passare il valore <xref:Microsoft.Build.Framework.BuildEventArgs>, o un derivato, come parametro.  
  
 Per ulteriori informazioni, vedere [la creazione di logger di inoltro](../msbuild/creating-forwarding-loggers.md).  
  
### <a name="attaching-a-distributed-logger"></a>Associare un Logger distribuito  
 Per associare un logger distribuito su una compilazione da riga di comando, utilizzare il `/distributedlogger` (o, `/dl` breve) passare. Il formato per specificare i nomi delle classi e tipi di logger sono identici a quelli per il `/logger` commutatore, ad eccezione del fatto che un logger distribuito è costituito da due classi di registrazione: un logger di inoltro e un logger centrale. Ecco un esempio di associare un logger distribuito:  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 Un asterisco (*) separa i due nomi dei logger nel `/dl` passare.  
  
## <a name="see-also"></a>Vedere anche  
 [Logger di compilazione](../msbuild/build-loggers.md)   
 [Creazione di logger di inoltro](../msbuild/creating-forwarding-loggers.md)
