---
title: "Uso di dati di metrica del codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codemetrics.output"
helpviewer_keywords: 
  - "risultati metrica codice"
  - "finestra Risultati metrica codice"
  - "finestra Risultati, metrica codice"
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 17
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 17
---
# Uso di dati di metrica del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La finestra **Risultati metrica codice** visualizza i dati generati dall'analisi della metrica del codice.  Per ulteriori informazioni sui valori dei dati di metrica del codice, vedere [Valori della metrica del codice](../code-quality/code-metrics-values.md).  
  
 Di seguito sono elencate le diverse sezioni di questo argomento:  
  
-   [Finestra Risultati metrica codice](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [Visualizzazione dei risultati di metrica del codice](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [Filtro dei risultati di metrica del codice](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [Aggiunta, rimozione e ridisposizione delle colonne di dati](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [Copiare dati negli Appunti o in Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [Creazione di un elemento di lavoro in base ai risultati metrici del codice](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Finestra Risultati metrica codice  
 Nella finestra **Risultati metrica codice** è presente una barra degli strumenti nella parte superiore e colonne per la visualizzazione dei risultati calcolati.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Gerarchia**|La colonna **Gerarchia** contiene una visualizzazione della struttura ad albero della gerarchia del codice, che è possibile espandere o comprimere per visualizzare il livello di dettaglio desiderato.  Nelle colonne rimanenti vengono visualizzati i risultati calcolati.  È possibile nascondere o disporre le colonne del risultato come si preferisce.|  
|**Gestibilità**|La colonna **Gestibilità** contiene un'icona oltre al risultato numerico.  Un'icona verde indica un livello di gestibilità relativamente alto.  Un'icona gialla indica un grado moderato di gestibilità.  Un'icona rossa indica bassa gestibilità e un potenziale punto problematico.  Questi indicatori di colore corrispondono a categorie di gravità utilizzate dalla regola FxCop AvoidUnmaintainableCode.  Questa regola genera un errore se l'indice di manutenibilità è inferiore a 10, un avviso se l'indice è compreso tra 10 e 20, né un errore né un avviso se l'indice e superiore a 20.  L'indice di manutenibilità è una sintesi di tre metriche: complessità ciclomatica, righe di codice e complessità computazionale.  I valori non sono espressi in unità.|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a> Visualizzazione dei risultati di metrica del codice  
 La finestra Risultati metrica codice viene visualizzata automaticamente quando vengono generati i risultati della metrica del codice.  È inoltre possibile visualizzarla in qualsiasi momento.  
  
#### Per visualizzare la finestra Risultati metrica codice  
  
-   Scegliere **Finestre** dal menu **Analizza** , quindi fare clic su **Risultati metrica codice**.  
  
     \-oppure\-  
  
-   Scegliere **Altre finestre** dal menu **Visualizza**, quindi selezionare  **Risultati metrica codice**.  
  
     La finestra Risultati metrica codice viene visualizzata anche quando non contiene risultati.  
  
#### Per visualizzare i dettagli sulla metrica del codice  
  
-   Se i risultati della metrica del codice sono stati generati, espandere la struttura ad albero nella colonna **Gerarchia**.  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a> Filtro dei risultati di metrica del codice  
 È possibile filtrare i risultati visualizzati nella finestra **Risultati metrica codice** mediante la barra degli strumenti che si trova nella parte superiore della finestra.  Ad esempio, può essere necessario visualizzare solo i risultati che presentano un indice di manutenibilità inferiore a 65.  
  
 La casella a discesa **Filtro** contiene i nomi delle colonne dei risultati.  Quando un filtro è definito, viene aggiunto con un rientro in fondo dell'elenco.  L'elenco può contenere gli ultimi dieci filtri definiti.  
  
#### Per filtrare i risultati della metrica del codice  
  
1.  Dall'elenco **Filtro**, selezionare il nome della colonna.  
  
2.  In **Min** digitare il valore minimo da visualizzare.  
  
3.  In **Max** digitare il valore massimo da visualizzare.  
  
4.  Scegliere il pulsante **Applica filtro**.  
  
5.  Per visualizzare i dettagli del risultato, espandere l'albero della gerarchia.  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> Aggiunta, rimozione e ridisposizione delle colonne di dati  
 È possibile aggiungere o rimuovere le colonne dei risultati dalla finestra **Risultati metrica codice**.  Inoltre, è possibile ridisporre le colonne dei risultati in modo che vengano visualizzate in base all'ordine desiderato.  
  
#### Per rimuovere una colonna  
  
1.  Fare clic sul pulsante **Aggiungi\/Rimuovi colonne**  
  
     \-oppure\-  
  
     Fare clic con il pulsante destro del mouse sull'intestazione di una colonna qualsiasi, quindi scegliere **Aggiungi\/Rimuovi colonne**.  
  
2.  Nella finestra di dialogo **Aggiungi\/Rimuovi colonne**, deselezionare la casella di controllo relativa alla colonna che si desidera rimuovere, quindi fare clic su **OK**.  
  
#### Per aggiungere una colonna rimossa in precedenza  
  
1.  Fare clic sul pulsante **Aggiungi\/Rimuovi colonne**  
  
     \-oppure\-  
  
     Fare clic con il pulsante destro del mouse sull'intestazione di una colonna qualsiasi, quindi scegliere **Aggiungi\/Rimuovi colonne**.  
  
2.  Nella finestra di dialogo **Aggiungi\/Rimuovi colonne**, selezionare la casella di controllo relativa alla colonna che si desidera aggiungere, quindi fare clic su **OK**.  
  
#### Per ridisporre le colonne  
  
1.  Fare clic sul pulsante **Aggiungi\/Rimuovi colonne**  
  
     \-oppure\-  
  
     Fare clic con il pulsante destro del mouse sull'intestazione di una colonna qualsiasi, quindi scegliere **Aggiungi\/Rimuovi colonne**.  
  
2.  Nella finestra di dialogo **Aggiungi\/Rimuovi colonne**, selezionare la colonna che si desidera spostare, quindi fare clic sulla freccia su o sulla freccia giù.  
  
3.  Quando la colonna si trova nella posizione desiderata, fare clic su **OK**.  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> Copiare dati negli Appunti o in Excel  
 È possibile selezionare e copiare una riga selezionata di dati metrici del codice negli Appunti come stringa di testo che contiene una riga per il nome e il valore di ciascuna colonna di dati.  È inoltre possibile fare clic su **Apri elenco in Microsoft Excel** per esportare tutti i risultati metrici nel codice in un foglio di calcolo di Excel  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> Creazione di un elemento di lavoro in base ai risultati metrici del codice  
 È possibile creare un [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] elemento di lavoro basato sui risultati nella finestra **Risultati metrici del codice**.  Quando viene creato l'elemento di lavoro, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornisce automaticamente un titolo nel campo **Titolo** e i dati metrici nella sezione **Cronologia**.  
  
 Per ulteriori informazioni sulla creazione di elementi di lavoro, vedere [Create a work item &#91;redirected&#93;](http://msdn.microsoft.com/it-it/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### Per creare un elemento di lavoro basato su un risultato  
  
1.  Fare clic con il pulsante destro del mouse sul risultato.  
  
2.  Selezionare **Crea elemento di lavoro**, quindi fare clic sul tipo di elemento di lavoro che si desidera creare. Ad esempio **Bug**, **Attività**e così via.  
  
3.  Compilare il form dell'elemento di lavoro specificando tutti i campi obbligatori.  
  
4.  Scegliere **Salva tutto** dal menu **File** per salvare l'elemento di lavoro.  
  
#### Per creare un bug basato su un risultato  
  
1.  Fare clic sul risultato per selezionarlo.  
  
2.  Fare clic sul pulsante **Crea elemento di lavoro**.  
  
3.  Compilare il form dell'elemento di lavoro specificando tutti i campi obbligatori.  
  
4.  Scegliere **Salva tutto** dal menu **File** per salvare l'elemento di lavoro.  
  
## Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Procedura: generare dati di metrica codice](../code-quality/how-to-generate-code-metrics-data.md)