---
title: "Visualizzazione Riepilogo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.summary"
helpviewer_keywords: 
  - "rapporti di prestazioni, Riepilogo (visualizzazione)"
  - "rapporti degli strumenti di profilatura, visualizzazione Riepilogo"
  - "strumenti di profilatura, visualizzazione Riepilogo"
  - "visualizzazione Riepilogo"
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 37
---
# Visualizzazione Riepilogo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Riepilogo vengono visualizzate informazioni sulle funzioni o sugli oggetti che influiscono maggiormente sulle prestazioni durante un'esecuzione di profilatura.  Questa visualizzazione fornisce un grafico cronologia e due o più elenchi delle funzioni o degli oggetti che influiscono maggiormente sulle prestazioni in base ai parametri di prestazioni del metodo di analisi.  I dati disponibili in questa visualizzazione dipendono dal metodo di profilatura utilizzato \(campionamento, strumentazione o concorrenza\) e dalla raccolta o meno di dati di allocazione di memoria .NET.  
  
 Per tutte le visualizzazioni Riepilogo, tranne la visualizzazione Riepilogo dei dati di concorrenza, il grafico cronologia nella visualizzazione Riepilogo rappresenta l'utilizzo del processore \(CPU\) dell'applicazione profilata durante il periodo di esecuzione del profilo.  
  
-   Se si specifica un intervallo di tempo sul grafico, è possibile analizzare di nuovo i dati dell'intervallo o ingrandire la visualizzazione della sequenza temporale per l'intervallo specificato.  Per ulteriori informazioni, vedere [Procedura: filtrare le visualizzazioni rapporto dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
-   È possibile fare clic su una funzione di un elenco di visualizzazione del riepilogo per visualizzare i Dettagli funzione per la funzione.  Si può anche fare clic con il pulsante destro del mouse sulla funzione per altre opzioni di visualizzazione.  
  
-   Per modificare il numero di elementi visualizzati negli elenchi della visualizzazione di riepilogo, scegliere **Opzioni** dal menu **Strumenti** e quindi selezionare **Strumenti di prestazioni**.  In **Impostazioni generali** modificare l'impostazione **Numero delle funzioni nella visualizzazione Riepilogo**.  
  
## Collegamenti alle notifiche  
 È possibile fare clic su collegamenti nell'elenco della Notifica per impostare opzioni di visualizzazione per il report.  L'elenco è a destra del grafico cronologia.  
  
|||  
|-|-|  
|**Mostra codice non utente**<br /><br /> **Mostra Just My Code**|Non disponibile per codice nativo o dati di analisi raccolti utilizzando il metodo di strumentazione.  Consente di passare dalla visualizzazione dei dati solo da codice utente \(**Mostra Just My Code**\) alla visualizzazione dei dati da tutto il codice, includendo il codice del sistema \(**Mostra codice non utente**\).  Per impostazione predefinita, i dati sono limitati al codice utente.  Per modificare l'impostazione, vedere [Procedura: Filtrare visualizzazioni report per visualizzare Just My Code](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|  
|**Visualizzare Linee guida**|Visualizza gli avvisi relativi alle regole di prestazioni nella finestra **Elenco errori**.  Per ulteriori informazioni, vedere [Utilizzo di regole per le prestazioni per analizzare dati](../profiling/using-performance-rules-to-analyze-data.md).|  
  
## Rapporto  
 È possibile fare clic su collegamenti nell'elenco del Report per aprire visualizzazioni diverse e confrontare, salvare o filtrare il report.  L'elenco è a destra del grafico cronologia.  
  
|||  
|-|-|  
|**Mostra struttura ad albero delle chiamate ridotta**|Visualizza i percorsi di esecuzione più dispendiosi della funzione utilizzati nella visualizzazione Struttura ad albero delle chiamate.  Per ulteriori informazioni, vedere [Visualizzazione Struttura ad albero delle chiamate](../profiling/call-tree-view.md).|  
|**Mostra riga critica**|Non disponibile per dati di analisi raccolti utilizzando il metodo di strumentazione.  Visualizza le righe del codice sorgente più dispendioso fiancheggia nella visualizzazione Righe.  Per ulteriori informazioni, vedere [Visualizzazione Righe](../profiling/lines-view.md).|  
|**Confronta report**|Visualizza la finestra di dialogo **Selezionare i file di analisi per il confronto**, in cui è possibile specificare un altro file dei dati di profilatura da confrontare con il file corrente.  Per ulteriori informazioni, vedere [Confronto di file di dati degli strumenti per la profilatura](../profiling/comparing-performance-data-files.md).|  
|**Esporta dati rapporto**|Visualizza la finestra di dialogo **Esporta report**, in cui è possibile specificare una o più visualizzazioni di report da salvare come file in formato csv \(comma\-separated value\) o xml.  Per ulteriori informazioni, vedere [How to: Export Profiling Tools Reports](http://msdn.microsoft.com/it-it/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Salvare rapporti analizzati**|Salva il file dei dati di analisi corrente come file .vsps, visualizzato più rapidamente nell'interfaccia per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Per ulteriori informazioni, vedere [How to: Save Analyzed Profiling Data Files](http://msdn.microsoft.com/it-it/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Filtra dati rapporto**|Visualizza il riquadro del filtro di rapporto profiler in cui è possibile specificare criteri per limitare i dati nella visualizzazione del rapporto.  Per ulteriori informazioni, vedere [Filtro di visualizzazione dei report degli strumenti per la profilatura](../profiling/performance-report-view-filter.md).|  
|**Attivare la modalità Schermo intero**|Attivare o disattivare la modalità schermo intero per la visualizzazione di report.|  
  
## Vedere anche  
 [Visualizzazione Riepilogo](../profiling/summary-view-sampling-data.md)   
 [Visualizzazione Riepilogo](../profiling/summary-view-instrumentation-data.md)   
 [Visualizzazione Riepilogo](../profiling/summary-view-dotnet-memory-data.md)