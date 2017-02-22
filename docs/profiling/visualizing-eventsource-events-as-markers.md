---
title: "Visualizzazione di eventi EventSource come marcatori | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione di eventi EventSource come marcatori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il visualizzatore della concorrenza può visualizzare gli eventi EventSource come marcatori, ed è possibile controllare come vengono visualizzati i marcatori.  Per visualizzare i marcatori EventSource, registrare il GUID del provider ETW tramite la finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Il visualizzatore di concorrenze ha convenzioni predefinite per rappresentare eventi EventSource come [Marcatori di flag](../profiling/flag-markers.md), [Marcatori di span](../profiling/span-markers.md)e [Marcatori di messaggi](../profiling/message-markers.md).  È possibile personalizzare la modalità con cui gli eventi EventSource vengono visualizzati aggiungendo campi personalizzati agli eventi.  Per ulteriori informazioni sui marcatori, vedere [Marcatori del visualizzatore di concorrenza](../profiling/concurrency-visualizer-markers.md).  Per ulteriori informazioni sugli eventi EventSource, vedere <xref:System.Diagnostics.Tracing>.  
  
## Visualizzazione predefinita degli eventi EventSource  
 Per impostazione predefinita, il visualizzatore della concorrenza utilizza le seguenti convenzioni per rappresentare gli eventi EventSource.  
  
### Tipo di marcatore  
  
1.  Eventi che hanno [Opcode](http://msdn.microsoft.com/it-it/d97953df-669b-4c55-b1a8-925022b339b7) win:Start o win:Stop vengono considerati come l'inizio o la fine di un intervallo, rispettivamente.  Gli intervalli annidati o sovrapposti non possono essere visualizzati.  Le coppie di eventi che iniziano in un thread e terminano in un altro non possono essere visualizzati.  
  
2.  Un evento il cui Opcode non è né win:Start né win:Stop viene considerato come flag del marcatore a meno che il suo [Livello](http://msdn.microsoft.com/it-it/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) \(campo di EVENT\_RECORD.EVENT\_HEADER.EVENT\_DESCRIPTOR\) non sia win:Verbose o superiore.  
  
3.  In tutti gli altri casi, l'evento viene considerato come un messaggio.  
  
### Importanza  
 La tabella riportata di seguito definisce il livello dell'evento corrisponde all'importanza del marcatore.  
  
|Livello ETW|Importanza del Visualizzatore di concorrenze|  
|-----------------|--------------------------------------------------|  
|win:LogAlways|Normal|  
|win:Critical|Livello critico|  
|win:Error|Livello critico|  
|win:Warning|High|  
|win:Informational|Normal|  
|win:Verbose|Low|  
|Maggiore di win:verbose|Low|  
  
### Nome della serie.  
 Il nome dell'attività dell'evento viene utilizzato per il nome della serie.  I nomi delle serie sono vuoti se nessuna attività è stata definita per l'evento.  
  
### Categoria  
 Se il livello è win:Critical o win:Error, la categoria è Alert \(\- 1\).  In caso contrario, la categoria è la predefinita \(0\).  
  
### Testo  
 Se un messaggio di testo formattato di tipo printf è stato definito per l'evento, viene visualizzato come descrizione del marcatore.  In caso contrario, la descrizione è il nome dell'evento e il valore di ogni campo del payload.  
  
## Personalizzare la visualizzazione degli eventi EventSource  
 È possibile personalizzare la modalità di visualizzazione degli eventi EventSource aggiungendo campi appropriati all'evento, come descritto nelle sezioni seguenti.  
  
### Tipo di marcatore  
 Utilizzare il campo `cvType`, un byte, per controllare il tipo di marcatore utilizzato per rappresentare l'evento.  Di seguito sono illustrati i valori disponibili per cvType:  
  
|Valore di cvType|Tipo del marcatore risultante|  
|----------------------|-----------------------------------|  
|0|Messaggio|  
|1|Inizio dell'intervallo|  
|2|Fine dell'intervallo|  
|3|Flag|  
|Tutti gli altri valori|Messaggio|  
  
### Importanza  
 È possibile utilizzare il campo `cvImportance`, un byte, per determinare l'importanza di un evento EventSource.  Tuttavia, si consiglia di verificare l'importanza visualizzata di un evento utilizzando il relativo livello.  
  
|Valore di cvImportance|Importanza del Visualizzatore di concorrenze|  
|----------------------------|--------------------------------------------------|  
|0|Normal|  
|1|Livello critico|  
|2|High|  
|3|High|  
|4|Normal|  
|5|Low|  
|Tutti gli altri valori|Low|  
  
### Nome della serie.  
 Utilizzare il campo `cvSeries` relativo all'evento, una stringa, per verificare il nome di una serie che il Visualizzatore della concorrenza fornisce ad un evento EventSource.  
  
### Categoria  
 Utilizzare il campo `cvCategory`, un byte, per controllare la categoria che il Visualizzatore della concorrenza fornisce ad un evento EventSource.  
  
### Testo  
 Utilizzare il campo `cvTextW`, una stringa, per controllare la descrizione che il Visualizzatore della concorrenza fornisce ad un evento EventSource.  
  
### SpanID  
 Utilizzare il campo cvSpanId, un int, per confrontare coppie di eventi.  Il valore per ogni coppia di eventi start\/stop che rappresentano un intervallo deve essere univoco.  In genere per il codice in modalità simultanea, questo richiede l'utilizzo di primitive di sincronizzazione come <xref:System.Threading.Interlocked.Exchange%2A> per assicurarsi che la chiave \(il valore che viene utilizzato per CvSpanID\) sia corretta.  
  
> [!NOTE]
>  L'utilizzo di SpanID per annidare gli intervalli, ne consente la loro sovrapposizione nello stesso thread, o ne consente l'inizio in un thread e la loro terminazione in un altro non è supportata.  
  
## Vedere anche  
 [Marcatori del visualizzatore di concorrenza](../profiling/concurrency-visualizer-markers.md)