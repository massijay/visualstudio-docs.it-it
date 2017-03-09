---
title: "Finestra di dialogo Impostazioni avanzate (visualizzatore di concorrenza) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.settings"
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Finestra di dialogo Impostazioni avanzate (visualizzatore di concorrenza)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Tramite la finestra di dialogo **Impostazioni avanzate** nel Visualizzatore di Concorrenza, è possibile controllare quali tracce vengono raccolte.  La finestra di dialogo ha delle schede per i simboli, Just My Code, il buffer, il filtro, gli eventi CLR, i marcatori, i provider e i file.  
  
## Simboli  
 Il Visualizzatore di Concorrenza utilizza le stesse impostazioni dei simboli del debugger di Visual Studio.  Il Visualizzatore di Concorrenza utilizza le impostazioni per risolvere gli stack di chiamate associati ai dati relativi alle prestazioni.  Quando elabora le tracce, il Visualizzatore di Concorrenza accede ai server di simboli specificati nella pagina delle impostazioni.  Quando questi dati sono accessibili tramite una rete, l'elaborazione della traccia rallenta.  Per ridurre il tempo richiesto per risolvere simboli, è possibile memorizzare i simboli nella cache in locale.  Se i simboli sono stati scaricati, Visual Studio li caricherà dalla cache locale.  
  
## Just My Code  
 Per impostazione predefinita, Just My Code è il set di file .exe e .dll associati alla soluzione corrente in Visual Studio.  Il Visualizzatore di Concorrenze esamina questo set di file quando si utilizza la funzionalità Just My Code per filtrare gli stack di chiamate.  Nella scheda Just My Code, è possibile aggiungere directory contenenti file EXE e i file DLL alle posizioni che il Visualizzatore di Concorrenze utilizza per Just My Code.  
  
 I percorsi di file EXE e file DLL vengono archiviati nel file di traccia quando la traccia viene raccolta.  Modificare questa impostazione non ha effetto sulle tracce precedentemente raccolte.  
  
## Buffering  
 Il Visualizzatore di Concorrenza utilizza Event Tracing per Windows \(ETW\) quando raccoglie una traccia.  ETW utilizza i vari buffer quando archivia gli eventi.  Le impostazioni predefinite del buffer ETW potrebbero non essere ottimali in tutti i casi e , in alcuni casi, potrebbe causare problemi come eventi persi.  È possibile utilizzare la scheda di buffer per configurare le impostazioni del buffer ETW.  Per ulteriori informazioni, vedere [Registrazione di eventi](http://go.microsoft.com/fwlink/?LinkId=234579) ed [Struttura di EVENT\_TRACE\_PROPERTIES](http://go.microsoft.com/fwlink/?LinkId=234580).  
  
## Filtro  
 Nella scheda di filtro, è possibile selezionare il set di eventi che il Visualizzatore di Concorrenza raccoglie.  Selezionare un sottoinsieme degli eventi limita i tipi di dati visualizzati nei rapporti, riduce la dimensione di ciascuna traccia e riduce il tempo necessario per processare le tracce.  
  
### Eventi CLR  
 Gli eventi generati da Common Language Runtime \(CLR\) consentono al Visualizzatore di concorrenza di risolvere gli stack di chiamate gestite.  Se si disabilita la raccolta di eventi CLR, la dimensione della traccia verrà ridotta, ma alcuni stack di chiamate non si risolveranno.  In seguito, qualche attività dei thread della CPU potrebbe essere suddivisa in categorie in modo errato.  
  
### Raccogli per processi nativi  
 Per impostazione predefinita, gli eventi CLR vengono raccolti solo quando un processo gestito viene profilato perché non sono generalmente necessari per i processi nativi.  In alcuni casi \(per esempio, quando un processo nativo ospita CLR\), potrebbe essere necessario raccogliere eventi CLR per un processo nativo.  In questo caso, selezionare la casella di controllo **Raccogli per processi nativi**.  
  
### Disabilita Eventi Rundown  
 Il CLR genera gli eventi da due provider: il runtime e il rundown.  Se si desidera raccogliere eventi runtime CLR, ma si desidera evitare di raccogliere eventi di rundown, selezionare la casella di controllo **Disabilita eventi rundown**.  Questo riduce la dimensione del file di traccia generato dalla raccolta, ma è possibile che alcuni stack non vengano risolti.  Per ulteriori informazioni, vedere [CLR ETW Providers](../Topic/CLR%20ETW%20Providers.md).  
  
### Eventi di esempio  
 È possibile utilizzare gli eventi di esempio per raccogliere gli stack di chiamate associati all'esecuzione del thread.  Questi eventi vengono raccolti circa una volta al millisecondo per i thread che sono in esecuzione nel processo corrente.  Se si disabilita la raccolta di eventi di esempio, la dimensione della traccia raccolta viene ridotta, ma non è possibile visualizzare nessuno stack di chiamate associati all'esecuzione di thread.  
  
### Eventi GPU  
 Gli eventi GPU sono eventi generati da DirectX.  Se si disabilita la raccolta di eventi GPU, la dimensione della traccia raccolta viene ridotta, ma non è possibile visualizzare alcuna attività GPU nella Visualizzazione Utilizzo, o l'attività del motore di DirectX nella Visualizzazione Thread.  
  
### Eventi di I\/O di file  
 Gli eventi di I\/O di file rappresentano gli accessi al disco per conto del processo corrente.  Se si disabilitano gli eventi di I\/O dei file, la dimensione della traccia viene ridotta, ma la Visualizzazione Thread non segnalerà alcuna informazione sui canali del disco o le operazioni del disco.  
  
## Markers  
 Nella scheda dei marcatori, è possibile configurare il set di provider ETW che sono mostrati come marcatori nel Visualizzatore di concorrenza.  Inoltre è possibile filtrare la raccolta del marcatore in base al livello di importanza e alla categoria ETW.  Se si utilizza [SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md) e si utilizza il proprio provider del marcatore, è possibile registrarlo qui affinché venga riportato nella Visualizzazione Thread.  
  
### Aggiunta di un nuovo provider  
 Se il codice utilizza [SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md) o genera gli eventi ETW che seguono la convenzione <xref:System.Diagnostics.Tracing.EventSource>, è possibile visualizzare questi eventi nel Visualizzatore di concorrenza registrandoli in questa finestra di dialogo.  
  
 Nel campo Nome, immettere un nome che descrive i tipi di eventi generati dal provider.  Nel campo GUID, immettere il GUID associato a questo provider. \(Un GUID associato ad ogni provider ETW\).  
  
 Facoltativamente, è possibile specificare se filtrare gli eventi da questo provider, in base alla categoria o al livello di importanza.  È possibile utilizzare il campo categoria per filtrare in base alle categorie del Visualizzatore di Concorrenza SDK.  Per fare questo, immettere una stringa delimitata da virgole di categorie o di intervalli di categorie.  Questo specifica le categorie di eventi nel provider corrente da visualizzare.  Se si aggiunge un provider <xref:System.Diagnostics.Tracing.EventSource>, è possibile utilizzare il campo categoria per filtrare la parola chiave ETW.  Poiché la parola chiave è una maschera di bit, è possibile utilizzare una stringa delimitata da virgole di interi per specificare quali bit della maschera sono impostati.  Ad esempio, "1,2" consente di impostare il primo e il secondo bit e si traduce in 6 decimale.  
  
 È possibile utilizzare l'elenco del livello di importanza per filtrare gli eventi che hanno un'importanza o livello ETW inferiori al valore specificato.  
  
### Configurazione di un provider esistente  
 Per modificare le impostazioni associate a un provider esistente, selezionarlo nell'elenco e quindi scegliere il pulsante **Modifica provider**.  È possibile modificare il nome, il GUID e le impostazioni del filtro.  
  
### Filtrare i dati del marcatore dai rapporti del Visualizzatore di concorrenza  
 Se non si desidera che i dati per un provider specifico vengano visualizzati nelle tracce successive, deselezionare la casella di controllo accanto al provider che si desidera rimuovere.  
  
## File  
 Nella scheda **File**, è possibile specificare la directory in cui i file di traccia vengono archiviati ogni volta che una traccia viene raccolta.  Il Visualizzatore di Concorrenza genera quattro file per ogni traccia che raccolga:  
  
-   Un file di log di tracciatura degli eventi \(ETL\) in modalità kernel \(\*.kernel.etl\)  
  
-   Un file di log di tracciatura degli eventi in modalità utente \(\*.user.etl\)  
  
-   Un file di dati del Visualizzatore di concorrenze \(\*.CVData\)  
  
-   Un file di traccia del Visualizzatore di concorrenze \(\*.CVTrace\)  
  
 I due file con estensione ETL archiviano i dati di traccia non elaborati mentre i due file del Visualizzatore di concorrenze archiviano i dati elaborati.  I file ETL non elaborati in genere non vengono utilizzati dopo un'operazione che una traccia viene elaborata.  Selezionare la casella di controllo **Elimina i file di log della traccia di eventi \(ETL\) dopo l'analisi** riduce la quantità di dati di traccia archiviati sul disco.  
  
## Vedere anche  
 [Just My Code](../profiling/just-my-code-threads-view.md)   
 [Marcatori del visualizzatore di concorrenza](../profiling/concurrency-visualizer-markers.md)