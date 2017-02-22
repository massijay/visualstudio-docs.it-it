---
title: "Procedura: utilizzare le transazioni per aggiornare il modello | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 7
caps.handback.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Procedura: utilizzare le transazioni per aggiornare il modello
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le transazioni garantisce che le modifiche apportate all'archivio siano considerate come gruppo.  Le modifiche che sono raggruppate è possibile eseguire il commit o istruzione o come una singola unità.  
  
 Ogni volta che il codice del programma modifica, aggiunge, o elimina qualsiasi elemento nell'archivio in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] L'sdk di visualizzazione e modellazione di, è necessario farlo in una transazione.  È necessario che esista un'istanza attiva di <xref:Microsoft.VisualStudio.Modeling.Transaction> associato all'archivio quando la modifica avviene.  Ciò vale per tutti gli elementi del modello, le relazioni, le forme, ai diagrammi e alle relative proprietà.  
  
 Il meccanismo di transazione consente di evitare degli stati incoerenti.  Se si verifica un errore durante una transazione, tutte le modifiche viene eseguito il rollback di.  Se l'utente esegue un comando di annullamento, ogni transazione recente viene trattata come singolo passaggio.  L'utente non può annullare le parti di una modifica recente, a meno che in modo esplicito non siano state inserite nelle transazioni separate.  
  
## aprire una transazione  
 Il metodo più pratico di gestire una transazione è con un oggetto `using` istruzione allegato a l  `try...catch` istruzione:  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 Se un'eccezione che estende l'oggetto finale `Commit()`si verifica durante le modifiche, quest'ultimo verrà reimpostato allo stato precedente.  Ciò consente di garantire che gli errori non lasciare il modello in uno stato incoerente.  
  
 È possibile eseguire qualsiasi numero di modifiche in una transazione.  È possibile aprire le nuove transazioni in una transazione attiva.  Le transazioni annidate devono eseguire il commit o hanno eseguito il rollback prima che la transazione contenitore termini.  Per ulteriori informazioni, vedere l'esempio relativo a <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> proprietà.  
  
 Per rendere modifiche permanenti, è necessario `Commit` la transazione prima che venga eliminato.  Se si verifica un'eccezione che non viene intercettata nella transazione, quest'ultimo verrà reimpostato allo stato precedente le modifiche.  
  
## Il rollback di una transazione  
 Per assicurarsi che l'archivio rimane in o viene ripristinato lo stato precedente la transazione, è possibile utilizzare una delle seguenti espedienti:  
  
1.  Generare un'eccezione che non viene intercettata nell'ambito della transazione.  
  
2.  In modo esplicito ha eseguito il rollback della transazione:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## Le transazioni non influiscono sugli oggetti non di Archivio  
 Le transazioni la regola solo lo stato dell'archivio.  Non è possibile annullare le modifiche parziali apportate agli elementi esterni quali file, i database, oggetti o dichiarato con tipi comuni all'esterno della definizione di modello DSL.  
  
 Se un'eccezione può lasciare tale modifica coerente con l'archivio, è necessario consente di gestire tale considerazione il gestore di eccezioni.  Un modo per garantire che le risorse esterne rimangano sincronizzate con gli oggetti dell'archivio è di accoppiare ogni oggetto esterno a un elemento nell'archivio utilizzando i gestori eventi.  Per ulteriori informazioni, vedere [I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## Le regole hanno generato alla fine di una transazione  
 Al termine di una transazione, prima della transazione venga eliminato, le regole associate agli elementi nell'archivio vengono generate.  Ogni regola è un metodo che si applica a un elemento del modello modificato.  Ad esempio, è “corregge su„ regole che aggiornano lo stato di una forma quando il relativo elemento del modello è stato modificato e che creano una forma quando un elemento di modello viene creato.  Non esiste un ordine di accensione specificato.  Una modifica apportata a una regola può generare un'altra regola.  
  
 È possibile definire le proprie regole.  Per ulteriori informazioni sulle regole, vedere [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).  
  
 Le regole non genera dopo un'operazione di annullamento, ripetizione, o un comando di ripristino.  
  
## contesto di transazione  
 Ogni transazione ha un dizionario in cui è possibile archiviare tutte le informazioni desiderate:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Questo risulta particolarmente utile per trasferire informazioni tra le regole.  
  
## stato di transazione  
 È necessario in alcuni casi evitare propagare una modifica se la modifica è causata annullamento o scorrendo una transazione.  Questa situazione può verificarsi, ad esempio, se si scrive un gestore di valore della proprietà che consente di aggiornare un altro valore nell'archivio.  Poiché l'operazione di annullamento reimposta tutti i valori nell'archivio sugli stati precedenti, non è necessario calcolare i valori aggiornati.  Utilizzare il codice seguente:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Le regole possono generare quando l'archivio inizialmente viene caricato da un file.  Per evitare rispondere a queste modifiche, utilizzare:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```