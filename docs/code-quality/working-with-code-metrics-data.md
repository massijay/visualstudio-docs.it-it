---
title: Utilizzo di dati di metrica codice | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39d45f5d43819dc418b6378d34a19e6af1d8ee12
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-code-metrics-data"></a>Uso di dati di metrica del codice
Il **risultati metrica codice** finestra Visualizza i dati generati dall'analisi della metrica del codice. Per ulteriori informazioni sui valori di dati di metrica codice, vedere [valori della metrica del codice](../code-quality/code-metrics-values.md).  
  
 Di seguito sono elencate le diverse sezioni di questo argomento:  
  
-   [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [Visualizzazione risultati metrica codice](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [Filtro risultati metrica codice](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [Aggiungere, rimuovere e ridisporre le colonne di dati](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [Copia dei dati negli Appunti o Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [Creazione di un elemento di lavoro in base ai risultati metrica codice](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window  
 Il **risultati metrica codice** finestra dispone di una barra degli strumenti nella parte superiore e le colonne da visualizzare i risultati calcolati.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Gerarchia**|Il **gerarchia** colonna viene visualizzata la struttura della gerarchia di codice che è possibile espandere o comprimere per visualizzare il livello di dettaglio desiderato. Le colonne rimanenti mostrano i risultati calcolati. È possibile nascondere o disporre le colonne di risultati desiderato.|  
|**Manutenibilità**|Il **manutenibilità** colonna contiene un'icona oltre al risultato numerico. Un'icona verde indica un livello relativamente elevato di gestibilità. Un'icona gialla indica un grado moderato di gestibilità. Un'icona rossa indica un potenziale punto problematico e gestibilità basso. Questi indicatori colore corrispondono alle categorie di gravità che vengono usate dalla regola FxCop AvoidUnmaintainableCode. Questa regola genera un errore se l'indice di manutenibilità è inferiore a 10, un avviso se l'indice è compreso tra 10 e 20 e non un errore né un avviso se l'indice è superiore a 20. L'indice di manutenibilità è una sintesi delle tre metriche: complessità ciclomatica, righe di codice e complessità del calcolo. I valori non sono espressi come unità.|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a>Visualizzazione risultati metrica codice  
 La finestra Risultati metrica codice viene visualizzata automaticamente quando si generano risultati metrica codice. È inoltre possibile visualizzare la finestra in qualsiasi momento.  
  
#### <a name="to-display-the-code-metrics-results-window"></a>Per visualizzare la finestra Risultati metrica codice  
  
-   Nel **Analizza** menu, fare clic su **Windows** e quindi fare clic su **risultati metrica codice**.  
  
     \- oppure -  
  
-   Nel **vista** dal menu **altre finestre** e quindi fare clic su **risultati metrica codice**.  
  
     Anche quando non contiene risultati, verrà visualizzata la finestra Risultati metrica codice.  
  
#### <a name="to-view-code-metrics-details"></a>Per visualizzare i dettagli sulla metrica del codice  
  
-   Se sono stati generati risultati metrica codice, espandere l'albero di **gerarchia** colonna.  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a>Filtro risultati metrica codice  
 È possibile filtrare i risultati vengono visualizzati di **risultati metrica codice** finestra utilizzando la barra degli strumenti nella parte superiore. Potrebbe ad esempio, si desidera visualizzare solo i risultati che includono un indice di manutenibilità inferiore a 65.  
  
 Il **filtro** casella di riepilogo a discesa contiene i nomi delle colonne di risultati. Quando viene definito un filtro, aggiungerlo alla fine dell'elenco con un rientro. L'elenco può contenere gli ultimi dieci filtri che sono stati definiti.  
  
#### <a name="to-filter-the-code-metrics-results"></a>Per filtrare i risultati della metrica codice  
  
1.  Dal **filtro** , selezionare il nome della colonna.  
  
2.  In **Min**, digitare il valore minimo da visualizzare.  
  
3.  In **Max**, digitare il valore massimo deve essere visualizzato.  
  
4.  Fare clic su di **Applica filtro** pulsante.  
  
5.  Per visualizzare i dettagli dei risultati, espandere l'albero gerarchico.  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a>Aggiungere, rimuovere e ridisporre le colonne di dati  
 È possibile aggiungere o rimuovere risultati le colonne di **risultati metrica codice** finestra. Inoltre, è possibile riorganizzare le colonne dei risultati in modo che vengano visualizzati nell'ordine in cui si desidera.  
  
#### <a name="to-remove-a-column"></a>Per rimuovere una colonna  
  
1.  Fare clic su di **Aggiungi/Rimuovi colonne** pulsante.  
  
     \- oppure -  
  
     Fare doppio clic su qualsiasi intestazione di colonna e quindi fare clic su **Aggiungi/Rimuovi colonne**.  
  
2.  Nel **Aggiungi/Rimuovi colonne** la finestra di dialogo, deselezionare il casella di controllo per la colonna che si desidera rimuovere e quindi fare clic su **OK**.  
  
#### <a name="to-add-a-previously-removed-column"></a>Per aggiungere una colonna rimossa in precedenza  
  
1.  Fare clic su di **Aggiungi/Rimuovi colonne** pulsante.  
  
     \- oppure -  
  
     Fare doppio clic su qualsiasi intestazione di colonna e quindi fare clic su **Aggiungi/Rimuovi colonne**.  
  
2.  Nel **Aggiungi/Rimuovi colonne** finestra di dialogo, selezionare la casella di controllo per la colonna che si desidera aggiungere e quindi fare clic su **OK**.  
  
#### <a name="to-rearrange-columns"></a>Per riordinare le colonne  
  
1.  Fare clic su di **Aggiungi/Rimuovi colonne** pulsante.  
  
     \- oppure -  
  
     Fare doppio clic su qualsiasi intestazione di colonna e quindi fare clic su **Aggiungi/Rimuovi colonne**.  
  
2.  Nel **Aggiungi/Rimuovi colonne** finestra di dialogo, selezionare la colonna che si desidera spostare e quindi fare clic sulla freccia in su o freccia in giù.  
  
3.  Quando la colonna si trova in cui si desidera, fare clic su **OK**.  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a>Copia dei dati negli Appunti o Excel  
 È possibile selezionare e copiare una riga selezionata di dati di metrica codice negli Appunti come una stringa di testo che contiene una riga per il nome e il valore di ogni colonna di dati. È anche possibile fare clic su **Apri elenco in Microsoft Excel** per esportare tutti i risultati della metrica codice in un foglio di calcolo di Excel  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a>Creazione di un elemento di lavoro in base ai risultati metrica codice  
 È possibile creare un [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] elemento di lavoro che si basa sul comporta il **risultati metrica codice** finestra. Quando viene creato l'elemento di lavoro, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inserisce automaticamente un titolo nel **titolo** dati di metrica del campo e il codice sotto il **cronologia** scheda.  
  
 Per ulteriori informazioni su come creare elementi di lavoro, vedere [creare un elemento di lavoro &#91; reindirizzato &#93;](http://msdn.microsoft.com/en-us/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>Per creare un elemento di lavoro basato su un risultato  
  
1.  Fare clic sul risultato.  
  
2.  Scegliere **Crea elemento di lavoro**, quindi fare clic sul tipo di elemento di lavoro che si desidera creare (**Bug**, **attività**e così via).  
  
3.  Completare il form elemento di lavoro con l'inserimento di tutti i campi obbligatori.  
  
4.  Nel **File** menu, fare clic su **Salva tutto** per salvare l'elemento di lavoro.  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>Per creare un bug basato su un risultato  
  
1.  Fare clic sul risultato per selezionarlo.  
  
2.  Fare clic su di **Crea elemento di lavoro** pulsante.  
  
3.  Completare il form elemento di lavoro con l'inserimento di tutti i campi obbligatori.  
  
4.  Nel **File** menu, fare clic su **Salva tutto** per salvare l'elemento di lavoro.  
  
## <a name="see-also"></a>Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Procedura: Generare dati di metrica codice](../code-quality/how-to-generate-code-metrics-data.md)