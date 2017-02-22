---
title: "Utilizzo della finestra di progettazione flusso di lavoro di una macchina a stati (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Attività EventDrivenActivity"
  - "Attività SetStateActivity"
  - "progettazione del flusso di lavoro della macchina a stati"
  - "flussi di lavoro macchina a stati, attività"
  - "flussi di lavoro macchina a stati, finestra di progettazione"
  - "Attività StateActivity"
  - "Attività StateFinalizationActivity"
  - "Attività StateInitializationActivity"
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Utilizzo della finestra di progettazione flusso di lavoro di una macchina a stati (legacy)
Quando si crea un nuovo progetto flusso di lavoro di macchina a stati in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] che fa riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], è possibile scegliere di utilizzare il modello di progetto legacy **Applicazione console flusso di lavoro macchina a stati** o **Libreria flusso di lavoro macchina a stati**.Se si sceglie uno di questi modelli di progetto della macchina a stati, la finestra di progettazione della macchina a stati viene presentata come interfaccia utente della finestra di progettazione del flusso di lavoro legacy.Per ulteriori informazioni sui modelli di progetto legacy di una macchina a stati, vedere [Procedura: creare applicazioni console flusso di lavoro di una macchina a stati \(legacy\)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) e [Procedura: creare una libreria del flusso di lavoro di macchina a stati \(legacy\)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).  
  
 Il flusso di lavoro di una macchina a stati è costituito da un set di stati.Uno stato è indicato come stato iniziale.Ogni stato può ricevere un determinato insieme di eventi.In base a un evento, può essere fatta una transizione a un altro stato.Il flusso di lavoro di una macchina a stati può avere uno stato finale.Quando viene effettuata una transizione allo stato finale, l'esecuzione del flusso di lavoro è completata.  
  
## Visualizzazioni della finestra di progettazione della macchina a stati  
 La finestra di progettazione della macchina a stati è una finestra di progettazione con figura a mano libera, ciò vuol dire che le attività possono essere spostate liberamente sull'area di progettazione.La finestra di progettazione della macchina a stati presenta due visualizzazioni: visualizzazione *di stato* e visualizzazione basata sugli *eventi*.  
  
 La visualizzazione di stato mostra le attività di stato e le attività basate sugli eventi che possono essere contenute all'interno di un'attività di stato.In questa visualizzazione, le transizioni da uno stato a un altro vengono rappresentate da righe che si estendono dall'attività basata sugli eventi in uno stato a un altro stato.È anche possibile creare transizioni tracciando una linea.Per tracciare la transizione, selezionare l'attività basata sugli eventi e quindi selezionare uno degli handle sull'attività e trascinarlo.Questa azione consente di tracciare una riga.Questa riga viene quindi allegata allo stato di destinazione, indicando una transizione tra stati.  
  
 Per accedere alla visualizzazione basata sugli eventi, fare doppio clic su un'attività basata sugli eventi.La finestra di progettazione che verrà visualizzata è molto simile alla finestra di progettazione del flusso di lavoro sequenziale.All'inizio della finestra di progettazione, una barra di navigazione illustra la gerarchia delle attività fino all'attività basata sugli eventi visualizzata.È possibile tornare alla visualizzazione di stato facendo clic su qualsiasi elemento nella gerarchia visualizzata.Se è stata tracciata una transizione da uno stato all’altro nella visualizzazione di stato e se si sta visualizzando la visualizzazione basata sugli eventi di quell'attività, un'attività di stato fissa verrà aggiunta all'attività basata sugli eventi.Se si modificano le proprietà dell'attività di stato fissa, questa modifica è riflessa nella visualizzazione di stato.  
  
## Attività del flusso di lavoro di una macchina a stati  
 Nella tabella seguente sono descritte le attività principali utilizzate nella finestra di progettazione del flusso di lavoro della macchina a stati.  
  
|Nome della casella degli strumenti|Attività|Descrizione|  
|----------------------------------------|--------------|-----------------|  
|**Stato**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Rappresenta uno stato in una macchina a stati; può contenere attività **StateActivity** aggiuntive.Per ulteriori informazioni, vedere [Utilizzo dell'attività StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Specifica una transizione a un nuovo stato.Per ulteriori informazioni, vedere [Utilizzo dell'attività SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Viene eseguita quando viene immesso uno stato; può contenere altre attività.Per ulteriori informazioni, vedere [Utilizzo dell'attività StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006).|  
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Esegue le attività contenute quando si esce da un’attività [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042).Per ulteriori informazioni, vedere [Utilizzo dell'attività StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Viene utilizzata per stati che si basano su un evento esterno per avviare l’esecuzione.L'attività **EventDrivenActivity** deve avere un'attività che implementa l'interfaccia [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) come prima attività figlio.Per ulteriori informazioni, vedere [Utilizzo dell'attività EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
  
 Il componente principale del flusso di lavoro della macchina a stati è l'attività [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042).Dato che gli eventi vengono acquisiti nei vari punti del flusso di lavoro della macchina a stati, vengono immessi stati diversi per gestire le attività associate agli eventi.Nel corso della durata del flusso di lavoro, il flusso di lavoro può uscire da e accedere a molti stati diversi.Questi stati sono connessi l'un l'altro tramite l'attività [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041).  
  
 Quando si trascina un nuovo **StateActivity** sull'area di progettazione del flusso di lavoro, è possibile aggiungere [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043) o attività **StateActivity** aggiuntive come attività figlio.  
  
> [!CAUTION]
>  Quando si utilizza la finestra di progettazione del flusso di lavoro della macchina a stati, per creare flussi di lavoro è necessario monitorare la struttura del flusso di lavoro che si sta progettando con la finestra di visualizzazione **Struttura documento**.La visualizzazione della struttura del flusso di lavoro della macchina a stati nella finestra di visualizzazione **Struttura documento** rispecchia il layout logico delle attività nel file di markup del flusso di lavoro.Il layout fisico delle attività del flusso di lavoro, così come vengono visualizzate nell'area di progettazione, potrebbe non rispecchiare il layout logico delle attività nel file di markup del flusso di lavoro.  
>   
>  Per aprire la finestra **Struttura documento**, selezionare **Altre finestre** dal menu **Visualizza**, quindi scegliere **Struttura documento**.  
  
## Vedere anche  
 [Procedura: creare applicazioni console flusso di lavoro di una macchina a stati \(legacy\)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)   
 [Procedura: creare una libreria del flusso di lavoro di macchina a stati \(legacy\)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)   
 [Flussi di lavoro macchina a stati](http://go.microsoft.com/fwlink?LinkID=65016)   
 [Utilizzo dell'attività StateActivity](http://go.microsoft.com/fwlink?LinkID=65083)   
 [Utilizzo dell'attività StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006)   
 [Utilizzo dell'attività StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008)   
 [Utilizzo dell'attività SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082)   
 [Utilizzo dell'attività EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)