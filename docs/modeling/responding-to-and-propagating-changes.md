---
title: "Risposta alle modifiche e propagazione delle modifiche | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, eventi"
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 24
caps.handback.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Risposta alle modifiche e propagazione delle modifiche
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando viene creato un elemento, viene eliminato o aggiornato, è possibile scrivere codice che passa la modifica ad altre parti del modello, o a risorse esterne quali file, i database, o altri componenti.  
  
## In questa sezione  
 Come indicazione, considerare queste tecniche nell'ordine seguente:  
  
|Tecnica|Scenari|Ulteriori informazioni|  
|-------------|-------------|----------------------------|  
|Definire una proprietà calcolata del dominio.|Una proprietà del dominio del cui valore è calcolato da altre proprietà nel modello.  Ad esempio, un prezzo che è la somma dei prezzi di elementi correlati.|[Proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md)|  
|Definire una proprietà personalizzata del dominio di archiviazione.|Una proprietà del dominio archiviata in altre parti del modello o esternamente.  Ad esempio, è possibile analizzare una stringa dell'espressione in una struttura ad albero nel modello.|[Proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md)|  
|Gestori di modifica di override come OnValueChanging e OnDeleting|Mantieni gli elementi diversi della sincronizzazione e mantenere i valori esterni in sincronia con il modello.<br /><br /> Limitare i valori a intervalli definiti.<br /><br /> Chiamato immediatamente prima di e dopo il valore della proprietà e altre modifiche.  È possibile terminare la modifica genera un'eccezione.|[Gestori di modifica del valore delle proprietà del dominio](../modeling/domain-property-value-change-handlers.md)|  
|Regole|È possibile definire regole che vengono accodate per l'esecuzione immediatamente prima della fine di una transazione in cui una modifica si è verificata.  Non vengono eseguiti sulla fase di annullamento o di ripetizione.  Utilizzarli per mantenere una parte dell'archivio dello sincronizzati con un altro.|[Le regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md)|  
|Eventi dell'archivio|L'archivio di modellizzazione fornisce le notifiche di eventi come aggiungere o rimuovere un elemento o un collegamento, o modificare il valore di una proprietà.  L'evento viene eseguito su annulla e la ripetizione.  Utilizzare gli eventi dell'archivio per aggiornare i valori che non sono nell'archivio.|[I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|eventi di .NET|Le forme dispongono di gestori eventi che soddisfano i clic del mouse e altri movimenti.  È necessario registrarsi per questi eventi per ogni oggetto.  La registrazione viene generalmente effettuata nell'override di InitializeInstanceResources e deve essere effettuata per ogni elemento.<br /><br /> Questi eventi in genere si verificano all'esterno di una transazione.|[Procedura: intercettare un clic su una forma o su un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|  
|regole limiti|Una regola limiti viene utilizzata in modo specifico vincolare i limiti di una forma.|[Le regole associate \(BoundsRules\) vincolano posizione e dimensione delle forme](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|regole di selezione|Le regole di selezione in particolare vincolano quali l'utente può selezionare.|[Procedura: accedere e vincolare la selezione corrente](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|Scegliere gli stati degli elementi del modello utilizzando le funzionalità delle forme e i connettori come shadow, picchi freccia, colore e pesi della riga e stile.|[Aggiornamento di forme e di connettori per riflettere il modello](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## **Confrontare le regole e gli eventi dell'archivio**  
 Modificare i notificatori, regole e gli eventi vengono eseguiti quando si verificano modifiche in un modello.  
  
 Le regole in genere si applicano alla transazione finale in cui si è verificata la modifica e gli eventi vengono applicate al termine delle modifiche in una transazione viene eseguito il commit.  
  
 Utilizzare gli eventi dell'archivio per sincronizzare il modello con gli oggetti fuori dell'archivio e le regole di mantenere la coerenza all'interno dell'archivio.  
  
-   **Creare regole personalizzate** Creare una regola personalizzata come classe derivata da una regola astratta.  È necessario anche avvisare il framework sulla regola personalizzata.  Per ulteriori informazioni, vedere [Le regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).  
  
-   **La sottoscrizione di eventi** Prima che sia possibile sottoscrivere un evento, creare un gestore eventi e un delegato.  Utilizzare quindi <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>proprietà da sottoscrivere l'evento.  Per ulteriori informazioni, vedere [I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
-   **annullare le modifiche** Quando si annulla una transazione, gli eventi vengono generati, ma le regole applicate.  Se una regola modifica un valore e annullare la modifica, il valore viene reimpostato al valore originale durante l'operazione di annullamento.  Quando viene generato un evento, è necessario modificare manualmente il valore al valore originale.  Per ulteriori informazioni sui transactons e undo, vedere [Procedura: utilizzare le transazioni per aggiornare il modello](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
-   Passaggio di argomenti alle regole e agli eventi   Entrambi gli eventi e regole vengono passati `EventArgs` parametro contenente informazioni su come modello è stato modificato.  
  
## Vedere anche  
 [Procedura: intercettare un clic su una forma o su un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)   
 [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)