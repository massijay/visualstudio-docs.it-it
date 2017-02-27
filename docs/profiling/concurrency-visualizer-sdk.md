---
title: "SDK del visualizzatore di concorrenza | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.sdk.about"
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# SDK del visualizzatore di concorrenza
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile modificare il codice sorgente utilizzando l'SDK del Visualizzatore di concorrenza per visualizzare informazioni aggiuntive nel Visualizzatore di concorrenza.  È possibile associare dati aggiuntivi alle fasi e agli eventi nel codice.  Queste visualizzazioni aggiuntive sono note come *marcatori*.  Per una procedura dettagliata introduttiva, vedere [Introduzione al Visualizzatore di concorrenze SDK](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## Proprietà  
 Le flag, gli intervalli e i messaggi dispongono di due proprietà: categoria e priorità.  Nella finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), è possibile utilizzare queste proprietà per filtrare il set di marcatori visualizzato.  Inoltre, queste proprietà influiscono sulla rappresentazione visiva dei marcatori.  Ad esempio, la dimensione delle flag viene utilizzata per rappresentare la priorità.  Inoltre, il colore viene utilizzato per indicare la categoria.  
  
## Utilizzo di base  
 Il Visualizzatore di concorrenza espone un provider predefinito che si può utilizzare per generare i marcatori.  Il provider è già registrato con il Visualizzatore di concorrenza e non è necessario eseguire alcuna operazione per far apparire i marcatori all'interno dell'interfaccia utente.  
  
### C\# e Visual Basic  
 In C\#, Visual Basic e altro codice gestito, viene utilizzato il provider predefinito chiamando <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>.  Esso espone quattro funzioni per la generazione dei marcatori: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A> e <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>.  Esistono overload multipli per queste funzioni, a seconda che si desiderino utilizzare le impostazioni predefinite per le proprietà.  L'overload più semplice accetta un solo parametro di tipo stringa che specifica la descrizione dell'evento.  La descrizione viene visualizzata nei report del Visualizzatore di concorrenza.  
  
##### Per aggiungere il supporto all'SDK ad un progetto C\# o Visual Basic  
  
1.  Sulla barra dei menù, scegliere **Analizza**, **Visualizzatore di concorrenza**, **Aggiungi SDK al progetto**.  
  
2.  Selezionare il progetto in cui si desidera accedere all'SDK quindi premere il pulsante **Aggiungi SDK al progetto selezionato**.  
  
3.  Aggiungere le importazioni oppure le istruzioni using al codice.  
  
    ```c#  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### C\+\+  
 In C\+\+, creare un oggetto [Classe marker\_series](../profiling/marker-series-class.md) e utilizzarlo per chiamare le funzioni.  La classe `marker_series` espone tre funzioni per la generazione dei marcatori, [Metodo marker\_series::write\_flag](../profiling/marker-series-write-flag-method.md), [Metodo marker\_series::write\_message](../profiling/marker-series-write-message-method.md) e [Metodo marker\_series::write\_alert](../profiling/marker-series-write-alert-method.md).  
  
##### Per aggiungere il supporto all'SDK ad un progetto C\+\+ o C  
  
1.  Sulla barra dei menù, scegliere **Analizza**, **Visualizzatore di concorrenza**, **Aggiungi SDK al progetto**.  
  
2.  Selezionare il progetto in cui si desidera accedere all'SDK quindi premere il pulsante **Aggiungi SDK al progetto selezionato**.  
  
3.  Per C\+\+, includere `cvmarkersobj.h`.  Per C, includere `cvmarkers.h`.  
  
4.  Aggiungere un'istruzione using al codice.  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Creare un nuovo oggetto `marker_series` e passarlo al costruttore di `span`.  
  
    ```cpp  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## Utilizzo Personalizzato  
 Per scenari avanzati, l'SDK del Visualizzatore di concorrenza espone un maggiore controllo.  Due concetti principali sono associati a scenari più avanzati: provider di marcatori e serie di marcatori.  I provider di marcatori sono dei provider ETW diversi \(ognuno con un GUID diverso\).  Le serie di marcatori sono canali seriali di eventi generati da un provider.  È possibile utilizzarli per organizzare gli eventi generati da un provider di marcatori.  
  
#### Per utilizzare un nuovo provider di marcatori in un progetto C\# o Visual Basic.  
  
1.  Creare un oggetto <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>.  Il costruttore accetta un GUID.  
  
2.  Per registrare il provider, aprire la finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) del Visualizzatore di concorrenza.  Selezionare la scheda **Marcatori** quindi premere il pulsante **Aggiungi nuovo provider**.  Nella finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), immettere il GUID utilizzato per creare il provider e una descrizione del provider.  
  
#### Per utilizzare un nuovo provider di marcatori in un progetto C\+\+ o C  
  
1.  Utilizzare la funzione `CvInitProvider` per inizializzare un PCV\_PROVIDER.  Il costruttore accetta un GUID\* ed un PCV\_PROVIDER\*.  
  
2.  Per registrare il provider, aprire la finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Selezionare la scheda **Marcatori** quindi premere il pulsante **Aggiungi nuovo provider**.  In questa finestra di dialogo, immettere il GUID utilizzato per creare il provider e una descrizione del provider.  
  
#### Per utilizzare una serie di marcatori in un progetto C\# o Visual Basic  
  
1.  Per utilizzare una nuova <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>, prima crearla utilizzando un oggetto <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> e quindi generare gli eventi del marcatore direttamente dalla nuova serie.  
  
    ```c#  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);  
    series1.WriteFlag(″My flag″);  
    ```  
  
    ```vb  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)  
    series1.WriteFlag(″My flag″)  
    ```  
  
#### Per utilizzare una serie di marcatori in un progetto C\+\+  
  
1.  Creare un oggetto `marker_series`.  È possibile generare eventi da questa nuova serie.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### Per utilizzare una serie di marcatori in un progetto C  
  
1.  Utilizzare la funzione `CvCreateMarkerSeries` per creare un PCV\_MARKERSERIES.  
  
    ```cpp  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[riferimento alla libreria C\+\+](../profiling/cpp-library-reference.md)|Descrive l'API del Visualizzatore di concorrenza per C\+\+.|  
|[riferimento alla libreria C](../profiling/c-library-reference.md)|Descrive l'API del Visualizzatore di concorrenza per C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Descrive l'API del Visualizzatore di concorrenza per il codice gestito.|  
|[Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)|Informazioni di riferimento relative a visualizzazioni e rapporti dei file di dati di profilatura generati tramite il metodo di concorrenza e che includono di dati di esecuzione di thread.|