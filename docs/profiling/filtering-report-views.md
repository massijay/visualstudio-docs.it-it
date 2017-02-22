---
title: "Filtrare visualizzazioni dei rapporti sugli strumenti di profilatura | Microsoft Docs"
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
  - "strumenti di profilatura, configurazione"
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Filtrare visualizzazioni dei rapporti sugli strumenti di profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile applicare filtri ai file dei dati di profilatura per ridurre i relativi dati disponibili nelle visualizzazioni del rapporto di prestazioni ed esportati in file di rapporti.  È possibile ridurre un report ai dati tra due valori di timestamp e ridurre i dati a processi e thread specifici.  È possibile salvare i filtri in un file, quindi creare un filtro in un altro file di dati di profilatura importando il filtro salvato.  
  
 È inoltre possibile ridurre un rapporto a un intervallo di tempo tramite la sequenza temporale grafica nella visualizzazione Riepilogo.  Vedere [Procedura: filtrare le visualizzazioni rapporto dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
 Per escludere codice di sistema e di terze parti da un rapporto, vedere [Procedura: Filtrare visualizzazioni report per visualizzare Just My Code](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)  
  
## Procedure  
  
#### Per creare un filtro di rapporto profiler  
  
1.  Se non viene visualizzata la finestra Filtro di visualizzazione dei rapporti di prestazioni, fare clic su **Mostra filtro** nella barra degli strumenti Visualizzazione rapporto di prestazioni.  
  
     Il filtro di visualizzazione dei rapporti di prestazioni è una tabella.  Ogni riga della tabella rappresenta una clausola del filtro.  È possibile aggiungere un numero qualsiasi di clausole a un filtro.  
  
2.  Per ogni clausola che si desidera aggiungere a un filtro, selezionare o immettere valori nei campi seguenti di una riga.  
  
    |Campo|Descrizione|  
    |-----------|-----------------|  
    |**And\/Or**|Selezionare **And** se questa clausola e la successiva devono essere entrambe soddisfatte per restituire un risultato.  Selezionare **Or** se questa clausola o la successiva deve essere soddisfatta per restituire un risultato.|  
    |**Campo**|Selezionare il campo del rapporto da utilizzare nella clausola di filtro dall'elenco visualizzato dei campi di dati.|  
    |**Operatore**|Selezionare l'operatore che specifica la relazione che si desidera impostare nella clausola tra il campo e il valore.<br /><br /> \=    Uguale a<br /><br /> \<\>  Diverso<br /><br /> \<    Minore di<br /><br /> \>    Maggiore di<br /><br /> \<\=  Minore di o uguale<br /><br /> \>\=  Maggiore di o uguale|  
    |**Valore**|Selezionare o immettere il valore da cercare.  Per alcuni campi è presente l'elenco dei valori disponibili.|  
  
#### Per creare un filtro di rapporto profiler dalla visualizzazione Rapporto contrassegni  
  
1.  Selezionare **Contrassegni** dall'elenco **Visualizzazione corrente** sulla barra degli strumenti Visualizzazione rapporto di prestazioni.  
  
     Viene visualizzato il rapporto profiler Contrassegni.  
  
2.  Selezionare l'ETW o il campionamento che si desidera utilizzare come punto iniziale del report.  
  
3.  Tenere premuto il tasto CTRL e fare clic sull'evento che si desidera utilizzare come punto finale del report.  
  
4.  Fare clic con il pulsante destro del mouse e quindi scegliere una delle seguenti opzioni:  
  
    -   **Aggiungi filtro in contrassegni** crea clausole di filtro che utilizzano la colonna Contrassegno come campo del filtro.  
  
    -   **Aggiungi filtro in timestamp** crea clausole di filtro che utilizzano la colonna Timestamp in millisecondi come campo del filtro.  
  
     Le due opzioni filtrano il file di dati corrente allo stesso punto iniziale e finale.  È possibile migliorare queste opzioni esportando il filtro e utilizzandolo in altri rapporti.  
  
#### Per caricare un filtro esistente da un file  
  
1.  Nella barra degli strumenti Visualizzazione rapporto di prestazioni fare clic su **Importa filtro**.  
  
     Verrà visualizzata la finestra di dialogo **Carica filtro**.  
  
2.  Specificare il percorso e il nome del file di filtro \(.vspf\) da caricare.  
  
#### Per eseguire un filtro  
  
-   Nella barra degli strumenti Visualizzazione rapporto di prestazioni fare clic su **Esegui filtro**.  
  
#### Per arrestare un filtro con un'esecuzione troppo prolungata  
  
-   Nella barra degli strumenti Visualizzazione rapporto di prestazioni fare clic su **Arresta filtro**.  
  
#### Per rimuovere un filtro su una visualizzazione di rapporto  
  
1.  Eliminare le righe di clausole in Filtro di visualizzazione dei rapporti di prestazioni.  
  
2.  Nella barra degli strumenti Visualizzazione rapporto di prestazioni fare clic su **Esegui filtro**.  
  
#### Per salvare un filtro in un file  
  
1.  Nella barra degli strumenti Visualizzazione rapporto di prestazioni fare clic su **Esporta filtro**.  
  
     Verrà visualizzata la finestra di dialogo **Salva filtro**.  
  
2.  Specificare il percorso e il nome del file di filtro \(.vspf\) da salvare.  
  
## Vedere anche  
 [Personalizzazione delle visualizzazioni dei rapporti sugli strumenti di profilatura](../profiling/customizing-performance-tools-report-views.md)