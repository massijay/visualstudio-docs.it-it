---
title: "Procedura: utilizzare l&#39;SDK dei marcatori del visualizzatore di concorrenza | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: utilizzare l&#39;SDK dei marcatori del visualizzatore di concorrenza
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come utilizzare il Visualizzatore di concorrenza SDK per creare intervalli e scrivere i flag, messaggi e avvisi.  
  
### <a name="to-use-c"></a>Utilizzo di C++  
  
1.  Aggiungere il supporto di Visualizzatore di concorrenza SDK all'applicazione. Per ulteriori informazioni, vedere [Visualizzatore di concorrenza SDK](../profiling/concurrency-visualizer-sdk.md).  
  
2.  Aggiungere un `include` istruzione e una `using` istruzione per il SDK.  
  
    ```cpp  
  
    #include <cvmarkersobj.h>  
    using namespace Concurrency::diagnostic;  
  
    ```  
  
3.  Aggiungere il codice per creare tre intervalli nella serie marcatore predefinito e la scrittura di un flag, un messaggio e un avviso, uno per ogni intervallo. I metodi per scrivere i flag, messaggi e gli avvisi sono membri di [marker_series](../profiling/marker-series-class.md) (classe). Il costruttore per il [span](../profiling/span-class.md) classe richiede un `marker_series` dell'oggetto, in modo che ogni estensione è associata a una serie di marcatori specifico. Oggetto `span` termina quando viene eliminata.  
  
    ```cpp  
  
    marker_series series;  
    span *flagSpan = new span(series, 1, _T("flag span"));  
    series.write_flag(_T("Here is the flag."));  
    delete flagSpan;  
  
    span *messageSpan = new span(series, 2, _T("message span"));  
    series.write_flag(_T("Here is the message."));  
    delete messageSpan;  
  
    span *alertSpan = new span(series, 3, _T("alert span"));  
    series.write_flag(_T("Here is the alert."));  
    delete alertSpan;  
  
    ```  
  
4.  Nella barra dei menu, scegliere **Analizza**, **concorrenze**, **inizia con il progetto corrente** per eseguire l'applicazione e visualizzare il Visualizzatore di concorrenza. Nella figura seguente mostra gli intervalli di tre e tre i marcatori nel Visualizzatore di concorrenza.  
  
     ![Visualizzatore di concorrenza con 3 marcatori e avvisi](../profiling/media/cvmarkersnative.png "CvMarkersNative")  
  
5.  Aggiungere codice per creare una serie di marcatori personalizzate chiamando il costruttore per `marker_series` che accetta un nome di stringa per la serie di marcatore.  
  
    ```cpp  
  
    marker_series flagSeries(_T("flag series"));  
    span *flagSeriesSpan = new span(flagSeries, 1, _T("flag span"));  
    flagSeries.write_flag(1, _T("flag"));  
    // Sleep to even out the display in the Concurrency Visualizer.  
    Sleep(50);  
    delete flagSeriesSpan;  
  
    marker_series messageSeries(_T("message series"));  
    span *messageSeriesSpan = new span(messageSeries, 1, _T("message span"));  
    messageSeries.write_message(1, _T("message"));  
    // Sleep to even out the display in the Concurrency Visualizer.  
    Sleep(50);  
    delete messageSeriesSpan;  
  
    ```  
  
6.  Avviare il progetto corrente per visualizzare il Visualizzatore di concorrenza. La serie di due marcatori vengono visualizzati nella propria corsie nella visualizzazione thread. La figura seguente mostra due nuovi intervalli.  
  
     ![Visualizzatore di concorrenza con 3 serie di marcatori personalizzati](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")  
  
### <a name="to-use-visual-basic-or-c"></a>Per utilizzare Visual Basic o C#  
  
1.  Aggiungere il supporto di Visualizzatore di concorrenza SDK all'applicazione. Per ulteriori informazioni, vedere [Visualizzatore di concorrenza SDK](../profiling/concurrency-visualizer-sdk.md).  
  
2.  Aggiungere un `using` o `Imports` istruzione per il SDK.  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
  
    ```  
  
    ```c#  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
3.  Aggiungere il codice per creare tre intervalli sulla serie marcatore predefinito e la scrittura di un flag, un messaggio e un avviso, uno per ogni intervallo. Si crea un <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Span> oggetto chiamando il metodo statico [EnterSpan](assetId:///EnterSpan?qualifyHint=False&autoUpgrade=True) metodo. Per scrivere la serie predefinita, utilizzare i metodi statici di scrittura del <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers> (classe).  
  
    ```vb  
  
    Dim flagSpan As Span = Markers.EnterSpan("flag span")  
    Markers.WriteFlag("Here is the flag.")  
    flagSpan.Leave()  
  
    Dim messageSpan As Span = Markers.EnterSpan("message span")  
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1)  
    Markers.WriteMessage("Here is a message")  
    messageSpan.Leave()  
  
    Dim alertSpan As Span = Markers.EnterSpan("alert span")  
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1)  
    Markers.WriteAlert("Here is an alert")  
    alertSpan.Leave()  
  
    ```  
  
    ```c#  
  
    Span flagSpan = Markers.EnterSpan("flag span");  
    Markers.WriteFlag("Here is the flag.");  
    flagSpan.Leave();  
  
    Span messageSpan = Markers.EnterSpan("message span");  
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1);  
    Markers.WriteMessage("Here is a message");  
    messageSpan.Leave();  
  
    Span alertSpan = Markers.EnterSpan("alert span");  
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1);  
    Markers.WriteAlert("Here is an alert");  
    alertSpan.Leave();  
    ```  
  
4.  Nella barra dei menu, scegliere **Analizza**, **concorrenze**, **inizia con il progetto corrente** per eseguire l'applicazione e visualizzare il Visualizzatore di concorrenza. Nella figura seguente mostra gli intervalli di tre e tre i marcatori nella visualizzazione thread del Visualizzatore di concorrenza.  
  
     ![Visualizzatore di concorrenza con marcatori e avvisi](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")  
  
5.  Aggiungere codice per creare una serie di marcatori cliente tramite il metodo statico <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.CreateMarkerSeries%2A> metodo. Il <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries> classe contiene metodi per la creazione di intervalli e la scrittura di flag, messaggi e avvisi.  
  
    ```vb  
  
    Dim flagSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series")  
    Dim flagSeriesSpan As Span = flagSeries.EnterSpan("flag span")  
    System.Threading.Thread.Sleep(1)  
    flagSeries.WriteFlag(1, "flag")  
    System.Threading.Thread.Sleep(1)  
    flagSeriesSpan.Leave()  
  
    Dim messageSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("message series")  
    Dim messageSeriesSpan As Span = messageSeries.EnterSpan("message span")  
    messageSeries.WriteMessage("message")  
    System.Threading.Thread.Sleep(1)  
    messageSeriesSpan.Leave()  
    ```  
  
    ```c#  
  
    MarkerSeries flagSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series");  
    Span flagSeriesSpan = flagSeries.EnterSpan("flag span");  
    System.Threading.Thread.Sleep(1);  
    flagSeries.WriteFlag(1, "flag");  
    System.Threading.Thread.Sleep(1);  
    flagSeriesSpan.Leave();  
  
    MarkerSeries messageSeries = Markers.DefaultWriter.CreateMarkerSeries("message series");  
    Span messageSeriesSpan = messageSeries.EnterSpan("message span");  
    messageSeries.WriteMessage("message");  
    System.Threading.Thread.Sleep(1);  
    messageSeriesSpan.Leave();  
    ```  
  
6.  Avviare il progetto corrente per visualizzare il Visualizzatore di concorrenza. La serie di tre marcatore vengono visualizzati nella propria corsie nella visualizzazione thread. La figura seguente mostra tre nuovi intervalli.  
  
     ![Visualizzatore di concorrenza con 3 serie di marcatori personalizzati](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")  
  
## <a name="see-also"></a>Vedere anche  
 [SDK del Visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md)