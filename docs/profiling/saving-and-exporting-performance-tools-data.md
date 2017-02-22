---
title: "Salvataggio ed esportazione dei dati degli strumenti per le prestazioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per le prestazioni, salvataggio ed esportazione di report"
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Salvataggio ed esportazione dei dati degli strumenti per le prestazioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo argomento descrive come salvare ed esportare i file di dati delle prestazioni.  
  
##  <a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> Procedura: salvare i file di dati delle prestazioni come file di report analizzato  
 È possibile salvare le visualizzazioni filtrate o non filtrate dei file di dati di profilatura \(estensione vsp\) come file di report analizzato \(estensione vsps\). Un file di report analizzato può essere visualizzato nella finestra di visualizzazione report ed è notevolmente più piccolo del file con estensione vsp originale. Non è possibile tuttavia applicare un filtro ai dati di un file con estensione vsps. È possibile creare un file di report analizzato da Esplora prestazioni senza aprire il file nell'ambiente di sviluppo integrato \(IDE\) oppure è possibile aprire e filtrare il file con estensione vsp e quindi salvare i risultati.  
  
#### Per salvare un report di prestazioni analizzato da Esplora prestazioni  
  
1.  In **Report** fare clic con il pulsante destro sul file dei dati di profilatura da analizzare e quindi fare clic su **Salva dati analizzati**.  
  
2.  Nella finestra di dialogo **Salva dati analizzati** specificare la directory e quindi digitare il nome del file.  
  
3.  Fare clic su **Salva**.  
  
#### Per salvare un report di prestazioni analizzato dalla finestra di visualizzazione report  
  
1.  Aprire il file di dati di profilatura \(con estensione vsp\) nella finestra di Visualizzazione report.  
  
2.  \(Facoltativo\) Applicare un filtro ai dati. Per altre informazioni, vedere [Filtro di visualizzazione dei report degli strumenti per la profilatura](../profiling/performance-report-view-filter.md).  
  
3.  Fare clic su **Salva dati analizzati** nella barra degli strumenti della finestra di visualizzazione report.  
  
4.  Nella finestra di dialogo **Salva dati analizzati** specificare la directory e quindi digitare il nome del file.  
  
5.  Fare clic su **Salva**.  
  
## Procedura: esportare i report degli strumenti per la profilatura in un file con estensione Xml o Csv  
 È possibile esportare una o più visualizzazioni di report da un file di dati di profilatura con estensione vsp o vsps come file delimitato da virgole o file XML. Filtrare i dati nella finestra di visualizzazione report prima dell'esportazione o esportare le visualizzazioni di report dell'intero file di dati dalla finestra **Esplora prestazioni**.  
  
> [!NOTE]
>  È anche possibile copiare e incollare le righe selezionate dalla finestra di visualizzazione report come valori separati da tabulazioni.  
  
#### Per esportare un report di prestazioni analizzato dalla finestra Esplora prestazioni  
  
1.  In **Esplora prestazioni** selezionare il report e quindi fare clic con il pulsante destro del mouse e selezionare **Esporta**.  
  
     Viene visualizzata la finestra di dialogo **Esporta report**.  
  
2.  Selezionare le visualizzazioni di report da esportare.  
  
3.  In **Utilizzare nei rapporti il prefisso** specificare il prefisso da aggiungere al nome del report.  
  
4.  In **Percorso rapporto esportato** specificare la directory.  
  
5.  In **Formato del rapporto esportato** selezionare \(Delimitato da virgole\) \(\*.csv\) o Dati XML \(\*.xml\).  
  
6.  Fare clic su **Esporta**.  
  
     Ogni visualizzazione del report viene salvata in un file separato denominato \<prefisso\>\_\<nome visualizzazione report\>.\< csv&#124;xml\>  
  
#### Per esportare i report di prestazioni dalla finestra di visualizzazione report  
  
1.  Aprire il file con estensione vsp nella finestra di visualizzazione report.  
  
2.  \(Facoltativo\) Applicare un filtro ai dati. Per altre informazioni, vedere [Filtro di visualizzazione dei report degli strumenti per la profilatura](../profiling/performance-report-view-filter.md).  
  
3.  Fare clic su **Esporta report** nella barra degli strumenti della finestra di visualizzazione report.  
  
4.  Selezionare le visualizzazioni di report da esportare.  
  
5.  In **Utilizzare nei rapporti il prefisso** specificare il prefisso da aggiungere al nome del report.  
  
6.  In **Percorso rapporto esportato** specificare la directory.  
  
7.  In **Formato del rapporto esportato** selezionare \(Delimitato da virgole\) \(\*.csv\) o Dati XML \(\*.xml\).  
  
8.  Fare clic su **Esporta**.  
  
     Ogni visualizzazione del report viene salvata in un file separato denominato \<prefisso\>\_\<nome visualizzazione report\>.\< csv&#124;xml\>  
  
## Vedere anche  
 [Utilizzo degli strumenti di profilatura](../profiling/performance-explorer.md)   
 [Analisi dei dati degli strumenti per la profilatura](../profiling/analyzing-performance-tools-data.md)   
 [Confronto di file di dati degli strumenti per la profilatura](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)