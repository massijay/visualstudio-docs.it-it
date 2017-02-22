---
title: "ActivityDesigner Switch&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.ModelItemKeyValuePair.UI"
  - "System.Activities.Statements.Switch`1.UI"
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
caps.handback.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner Switch&lt;T&gt;
L'attività <xref:System.Activities.Statements.Switch%601> valuta un'espressione specificata e viene eseguita da una raccolta di attività la cui chiave associata corrisponde al valore ottenuto dalla valutazione.  
  
 L'ActivityDesigner **Switch\<T\>** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.Switch%601> in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## Attività Switch\<T\>  
 Un'attività <xref:System.Activities.Statements.Switch%601> contiene un oggetto <xref:System.Activities.Statements.Switch%601.Expression%2A> e un dizionario di <xref:System.Activities.Statements.Switch%601.Cases%2A>.Ogni case del dizionario è formato da una coppia contenente un parametro *key* e un'attività che funge da relativo parametro *value*.L'attività <xref:System.Activities.Statements.Switch%601> valuta <xref:System.Activities.Statements.Switch%601.Expression%2A> e lo confronta con ogni chiave.Se viene rilevata una corrispondenza, viene eseguita l'attività corrispondente.È consentita una sola corrispondenza in quanto le chiavi del dizionario devono essere univoche in base al tipo di uguaglianza definito dall'operatore di confronto di uguaglianza del dizionario.Se non vengono rilevate corrispondenze, viene eseguita l'attività <xref:System.Activities.Statements.Switch%601.Default%2A>.  
  
## Come utilizzare l'ActivityDesigner Switch\<T\>  
 L'ActivityDesigner **Switch\<T\>** è disponibile nella categoria **Flusso di lavoro** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, è possibile selezionare **Barra degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X. Dopo averlo rilasciato in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], visualizza la finestra di dialogo **Seleziona tipi** che consente di specificare il tipo generico *T* utilizzato nell'attività <xref:System.Activities.Statements.Switch%601>.Il valore predefinito è **Int32**.Dopo aver selezionato il tipo generico *T*, viene aggiunta una finestra di progettazione **Switch\<T\>** alla finestra di progettazione dei flussi di lavoro.  
  
 Di seguito sono riportate le proprietà della finestra di progettazione **Switch\<T\>**.Tutte le proprietà possono essere modificate nella griglia delle proprietà.Alcune di esse possono anche essere modificate nell'area della finestra di progettazione.  
  
 Nella tabella seguente vengono mostrate le proprietà <xref:System.Activities.Statements.Switch%601> più utili e viene illustrato come utilizzarle nella finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Switch%601>.Il valore predefinito è Switch\<Int32\>.Il valore può essere modificato nella finestra **Proprietà** o direttamente nell'intestazione della finestra di progettazione.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'utilizzo.|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Specifica l'espressione utilizzata per confrontare le chiavi presenti nella raccolta di case al fine da identificare il case da eseguire.|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Se non vengono rilevate corrispondenze, specifica l'attività eseguita.Fare clic sul pulsante **Aggiungi attività** nella finestra di progettazione per aprire la casella **Predefinita** in cui è possibile rilasciare l'attività.|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Specifica i case da valutare.Per aggiungere un case, fare clic sul pulsante **Aggiungi nuovo case** nella parte inferiore della finestra di progettazione **Switch\<T\>**.Il pulsante diventa una casella di testo o una casella combinata se il tipo generico selezionato durante l'aggiunta di Switch\<T\> è String o Enum.Dopo aver aggiunto una chiave alla casella **Valore case**, l'area del case si espande ed è possibile rilasciare un'attività nella posizione del testo di suggerimento "Rilasciare l'attività" per definire la logica di esecuzione del case.|  
  
 È possibile aggiungere più case, purché le relative chiavi non siano duplicate.In caso contrario, viene visualizzata una finestra di dialogo di errore in cui viene segnalato che la chiave del case specificata esiste già e che è necessario sceglierne un'altra.Nella finestra di progettazione **Switch\<T\>** può essere visualizzata in modalità espansa l'area di un solo case alla volta.Se l'area di un case si trova in modalità compressa, fare clic su di essa per espanderla.Si noti che, per un case compresso, nella finestra di progettazione viene mostrato l'eventuale nome visualizzato dell'attività a destra all'interno del case.In caso contrario, viene visualizzato il pulsante **Aggiungi attività** che consente di espandere il case facendo clic su di esso e di aggiungere un'attività.  
  
 Fare clic sulla chiave del case esistente per trasformarla da etichetta in casella di testo in modo che sia possibile modificarla.  
  
 È possibile eliminare un case in due modi.  
  
1.  Selezionare il case ed eliminarlo.  
  
2.  Selezionare il case, fare clic con il pulsante destro del mouse per visualizzare il menu di scelta rapida e scegliere **Elimina**.  
  
 Si noti che è necessario selezionare il case per eliminarlo.La selezione e la deselezione dell'attività in un case riguardano la sola attività e non il case.  
  
## Vedere anche  
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)