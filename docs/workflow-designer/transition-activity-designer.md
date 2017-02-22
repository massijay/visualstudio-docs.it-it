---
title: "ActivityDesigner Transition | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Transition.UI"
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "sdanie"
manager: "erikre"
---
# ActivityDesigner Transition
<xref:System.Activities.Statements.Transition> rappresenta la transizione tra due stati.  
  
## Utilizzo di ActivityDesigner Transition  
 Un ActivityDesigner Transition consente di configurare una transizione tra due stati.  
  
### Proprietà di transizione in Progettazione flussi di lavoro  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Transition> che possono essere impostate utilizzando la progettazione flussi di lavoro e ne viene descritta la modalità di utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Transition>.Il valore predefinito è **T1**.Il valore può essere modificato nella griglia della proprietà, nell'intestazione della finestra di progettazione estesa di transizione e nell'intestazione della sezione di azione all'interno della finestra di progettazione estesa di transizione.<xref:System.Activities.Activity.DisplayName%2A> è utilizzato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'utilizzo.|  
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|Se presente, specifica un'espressione che deve restituire **True** prima che il controllo venga passato allo stato di destinazione.Tale condizione può essere modificata nella griglia delle proprietà e nella finestra di progettazione estesa di transizione.Più condizioni in una transizione condivisa vengono valutate nell'ordine in cui appaiono nella finestra di progettazione di transizione. **Note:**  Si noti che se <xref:System.Activities.Statements.Transition.Condition%2A> di una transizione restituisce **False** \(o tutti gli stati di una transizione trigger condivisa restituiscono **False**\), la transizione non si verificherà e tutti i trigger per tutte le transizioni dallo stato verranno rinviati.In questa esercitazione, questa situazione non può verificarsi a causa della modalità con cui le condizioni vengono configurate \(esistono azioni specifiche per verificare se il valore indicato è corretto o errato\).|  
|**Origine**|True|Indica lo stato da cui ha origine questa transizione.Facendo clic sul nome dello stato di origine si passa dalla visualizzazione Progettazione a una visualizzazione estesa di tale stato.Questo valore viene impostato quando la transizione viene creata e non può essere modificata.|  
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|Specifica l'attività il cui completamento avvia la transizione.Per impostare questa attività, trascinarne una dalla **Casella degli strumenti** e rilasciarla nella sezione **Trigger** della transizione.|  
|<xref:System.Activities.Statements.Transition.Action%2A>|False|Specifica l'attività che viene eseguita quando le attività del trigger vengono completate e <xref:System.Activities.Statements.Transition.Condition%2A>, se presente, restituisce **true**.Questa attività viene eseguita durante la transizione allo stato di destinazione, dopo l'esecuzione dell'attività di <xref:System.Activities.Statements.State.Exit%2A> per lo stato di origine, se presente.Quando la finestra di progettazione di transizione viene espansa, questo valore può essere impostato trascinando un'attività da **Casella degli strumenti** e rilasciandola nella sezione **Azione** della transizione.Possono essere presenti più azioni per una sola transizione.Le singole azioni possono essere espanse e contratte e possono essere ordinate facendo clic sulla freccia verso l'alto o verso il basso visualizzato sull'azione quando sono presenti più azioni in una transizione.|  
|**Destinazione**|True|Indica lo stato in cui si trova la macchina a stati dopo il completamento della transizione.Ciò corrisponde alla proprietà <xref:System.Activities.Statements.Transition.To%2A> della transizione nel modello a oggetti.Facendo clic sul nome dello stato di destinazione si passa dalla visualizzazione Progettazione a una visualizzazione estesa di tale stato.Questo valore viene impostato quando viene creata la transizione e può essere modificato trascinando la freccia che connette la transizione allo stato di destinazione nella finestra di progettazione.|  
  
### Creazione transizioni  
 Le transizioni vengono creati trascinando una riga da uno stato a un altro, o rilasciando uno stato sui triangoli visualizzati quando lo stato viene trascinato su un altro stato.Per creare una transizione tramite l'operazione di trascinamento, posizionare il mouse sul bordo dello stato di origine e trascinare una linea dallo stato di origine allo stato di destinazione.Per creare una transizione tramite l'operazione di trascinamento, trascinare lo stato di destinazione e posizionarlo sullo stato di origine e rilasciarlo su uno dei quattro triangoli visualizzati intorno allo stato di origine.Lo stato di destinazione può essere un nuovo stato trascinato dalla **Casella degli strumenti**, o uno stato esistente trascinato dalla Progettazione flussi di lavoro.  
  
> [!NOTE]
>  Un singolo stato in una macchina a stati può essere composto da un massimo di 76 transizioni create mediante Progettazione flussi di lavoro.Il limite alle transizioni per uno stato per i flussi di lavoro creati all'esterno della finestra di progettazione è stabilito solo dalle risorse di sistema.  
  
 Le transizioni del trigger condivise sono il set di transizioni che condividono lo stesso evento del trigger.Un trigger condiviso consente la progressione condizionale a uno stato di destinazione in base alla valutazione delle espressioni configurate per più transizioni che condividono un evento comune del trigger.Per aggiungere altre azioni a una transizione e creare una transizione condivisa, fare clic sul cerchio che indica l'inizio della transizione desiderata e trascinarlo nello stato desiderato.La nuova transizione condividerà uno stesso trigger della transizione iniziale, ma avrà una condizione e un'azione univoche.Le transizioni condivise possono essere inoltre create dalla finestra di progettazione della transizione facendo clic su **Aggiungi transizione del trigger condivisa** nella parte inferiore della finestra di progettazione della transizione e selezionando lo stato di destinazione desiderato dall'elenco a discesa **Stati disponibili per la connessione**.  
  
## Vedere anche  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [State](../workflow-designer/state-activity-designer.md)