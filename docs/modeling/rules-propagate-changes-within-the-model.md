---
title: "Le regole propagano le modifiche all&#39;interno del modello | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, i modelli di dominio di programmazione"
  - "Linguaggio specifico di dominio, le regole"
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 30
caps.handback.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Le regole propagano le modifiche all&#39;interno del modello
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile creare una regola di archivio per propagare una modifica da un elemento a un altro in Visualization and Modeling SDK \(VMSDK\). Quando si verifica una modifica a qualsiasi elemento nell'archivio, le regole vengono pianificate da eseguire, in genere, quando viene eseguito il commit della transazione più esterna. Esistono diversi tipi di regole per diversi tipi di eventi, ad esempio l'aggiunta di un elemento o l'eliminazione. È possibile collegare regole a tipi specifici di elementi, forme o diagrammi. Molte funzioni incorporate sono definiti da regole: ad esempio, regole, verificare che un diagramma viene aggiornato quando cambia il modello. È possibile personalizzare il linguaggio specifico di dominio mediante l'aggiunta di regole personalizzate.  
  
 Archivio regole sono particolarmente utili per la propagazione delle modifiche all'interno dell'archivio, vale a dire le modifiche a elementi del modello, relazioni, forme o connettori e relativo dominio di proprietà. Le regole non vengono eseguiti quando l'utente richiama i comandi di annullamento o ripristino. Al contrario, il gestore delle transazioni garantisce che il contenuto dell'archivio viene ripristinato allo stato corretto. Se si desidera propagare le modifiche alle risorse all'esterno dell'archivio, utilizzare gli eventi di archiviazione. Per altre informazioni, vedere [I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Ad esempio, si supponga che si desidera specificare che ogni volta che l'utente \(o il codice\) crea un nuovo elemento di tipo ExampleDomainClass, viene creato un ulteriore elemento di un altro tipo in un'altra parte del modello. È possibile scrivere un AddRule e associarlo a ExampleDomainClass. Scrivere il codice nella regola per creare l'elemento aggiuntiva.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with a domain class:  
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class MyAddRule : AddRule  
 {  
  // Override the abstract method:  
  public override void ElementAdded(ElementAddedEventArgs e)  
  {  
    base.ElementAdded(e);  
    ExampleDomainClass element = e.ModelElement;  
    Store store = element.Store;  
    // Ignore this call if we're currently loading a model:  
    if (store.TransactionManager.CurrentTransaction.IsSerializing)   
       return;  
  
    // Code here propagates change as required – for example:  
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);  
      echo.Name = element.Name;  
      echo.Parent = element.Parent;    
    }  
  }  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
   protected override Type[] GetCustomDomainModelTypes()  
   {  
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
     types.Add(typeof(MyAddRule));  
     // If you add more rules, list them here.   
     return types.ToArray();  
   }  
 }  
}  
  
```  
  
> [!NOTE]
>  Il codice di una regola deve modificare lo stato solo degli elementi all'interno dell'archivio; vale a dire, la regola cambiano solo gli elementi del modello, relazioni, forme, connettori, diagrammi o le relative proprietà. Se si desidera propagare le modifiche alle risorse all'esterno dell'archivio, definire archiviare gli eventi. Per altre informazioni, vedere [I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
### Per definire una regola  
  
1.  Definire la regola come prefisso di una classe con il `RuleOn` attributo. L'attributo associa la regola a una delle classi di dominio o relazioni, elementi del diagramma. La regola verrà applicata a ogni istanza di questa classe, che può essere astratta.  
  
2.  Registrare la regola aggiungendolo al set restituito da `GetCustomDomainModelTypes()` nella classe del modello di dominio.  
  
3.  Derivare la classe di regola da una delle classi astratte di regola e scrivere il codice del metodo di esecuzione.  
  
 Nelle sezioni seguenti vengono descritti più dettagliatamente questi passaggi.  
  
### Per definire una regola in una classe di dominio  
  
-   In un file di codice personalizzato, definire una classe e prefisso di <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> attributo:  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   Il tipo di oggetto nel primo parametro può essere una classe di dominio, relazione di dominio, forma, connettore o diagramma. In genere, applicare regole a relazioni e le classi di dominio.  
  
     Il `FireTime` è in genere `TopLevelCommit`. Ciò garantisce che la regola viene eseguita solo dopo avere apportate tutte le modifiche principali della transazione. Le alternative sono Inline, che esegue la regola subito dopo la modifica. e LocalCommit, che esegue la regola alla fine della transazione corrente \(che potrebbe non essere quello più esterno\). È inoltre possibile impostare la priorità di una regola per influire sul relativo ordine nella coda, ma si tratta di un metodo affidabile per ottenere il risultato desiderato.  
  
-   È possibile specificare una classe astratta come tipo di oggetto.  
  
-   La regola si applica a tutte le istanze della classe dell'oggetto.  
  
-   Il valore predefinito per `FireTime` è TimeToFire.TopLevelCommit. In questo modo la regola da eseguire quando viene eseguito il commit della transazione più esterna. In alternativa, è TimeToFire.Inline. In questo modo la regola deve essere eseguito subito dopo l'evento di attivazione.  
  
### Per registrare la regola  
  
-   Aggiungere l'elenco di tipi restituiti dalla classe di regola `GetCustomDomainModelTypes` nel modello di dominio:  
  
    ```  
    public partial class ExampleDomainModel  
     {  
       protected override Type[] GetCustomDomainModelTypes()  
       {  
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
         types.Add(typeof(MyAddRule));  
         // If you add more rules, list them here.   
         return types.ToArray();  
       }  
     }  
  
    ```  
  
-   Se non si è certi del nome della classe del modello di dominio, cercare all'interno del file **Dsl\\GeneratedCode\\DomainModel.cs**  
  
-   Scrivere il codice in un file di codice personalizzato nel progetto DSL.  
  
### Per scrivere il codice della regola  
  
-   Derivare la classe di regola da una delle classi di base seguenti:  
  
    |Classe base|Trigger|  
    |-----------------|-------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|Viene aggiunto un elemento, un collegamento o una forma.<br /><br /> Consente di rilevare nuove relazioni, oltre a nuovi elementi.|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|Un valore di proprietà di dominio viene modificato. L'argomento del metodo fornisce i valori vecchi e nuovi.<br /><br /> Per le forme, questa regola viene attivata quando l'oggetto incorporato `AbsoluteBounds` le modifiche alle proprietà, se la forma viene spostata.<br /><br /> In molti casi, è più pratico eseguire l'override `OnValueChanged` o `OnValueChanging` nel gestore di proprietà. Questi metodi vengono chiamati immediatamente prima e dopo la modifica. Al contrario, la regola viene eseguita in genere alla fine della transazione. Per altre informazioni, vedere [Gestori di modifica del valore delle proprietà del dominio](../modeling/domain-property-value-change-handlers.md). **Note:**  Questa regola non viene generata quando viene creato o eliminato un collegamento. Invece di scrivere un `AddRule` e `DeleteRule` per la relazione di dominio.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|Generato quando un elemento o un collegamento sta per essere eliminata. La proprietà ModelElement.IsDeleting vale fino alla fine della transazione.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|Eseguito quando un elemento o un collegamento è stato eliminato. La regola viene eseguita dopo che sono state eseguite tutte le altre regole, tra cui DeletingRules. ModelElement.IsDeleting è false, e ModelElement.IsDeleted è true. Per consentire un annullamento successive, l'elemento non viene effettivamente rimosso dalla memoria, ma viene rimosso da Store.ElementDirectory.|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|Un elemento viene spostato dalla partizione di un archivio a un altro.<br /><br /> Si noti che questo non è correlato alla posizione di una forma grafica.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|Questa regola si applica solo alle relazioni di dominio. Viene attivata se si assegna in modo esplicito un elemento del modello a delle estremità di un collegamento.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|Generato quando l'ordine dei collegamenti a o da un elemento viene modificato utilizzando i metodi MoveBefore o MoveToIndex su un collegamento.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|Eseguito quando viene creata una transazione.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|Eseguito quando la transazione sta per essere eseguito il commit.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|Eseguito quando sta per eseguire il rollback della transazione.|  
  
-   Ogni classe dispone di un metodo che si esegue l'override. Tipo `override` nella classe per individuarlo. Il parametro di questo metodo identifica l'elemento che viene modificato.  
  
 Tenere presente i punti seguenti regole:  
  
1.  Il set di modifiche in una transazione possa generare molte regole. In genere, le regole vengono eseguite quando viene eseguito il commit della transazione più esterna. Vengono eseguiti in un ordine non specificato.  
  
2.  Una regola viene sempre eseguita all'interno di una transazione. Pertanto, non è necessario creare una nuova transazione per apportare modifiche.  
  
3.  Le regole non vengono eseguite quando viene eseguito il rollback di una transazione, o quando vengono eseguite le operazioni di annullamento o ripristino. Queste operazioni di ripristinare lo stato precedente di tutto il contenuto dell'archivio. Pertanto, se la regola viene modificato lo stato di tutti gli elementi all'esterno dell'archivio, potrebbe non tenere synchronism con l'archivio contenuto. Per aggiornare lo stato all'esterno dell'archivio, è preferibile utilizzare gli eventi. Per altre informazioni, vedere [I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
4.  Alcune regole vengono eseguite quando un modello viene caricato dal file. Per determinare se è in corso il caricamento o salvataggio, utilizzare `store.TransactionManager.CurrentTransaction.IsSerializing`.  
  
5.  Se il codice della regola crea più trigger di regola, verrà aggiunto alla fine dell'elenco di generazione dell'evento e verrà eseguiti prima del completamento della transazione. DeletedRules vengono eseguiti dopo tutte le altre regole. Una regola è possibile eseguire più volte in una transazione, una volta per ogni modifica.  
  
6.  Per passare informazioni da e verso le regole, è possibile archiviare informazioni di `TransactionContext`. Questo è solo un dizionario che viene mantenuto durante la transazione. Viene eliminato al termine della transazione. Gli argomenti dell'evento in ogni regola di accesso a esso. Tenere presente che le regole non vengono eseguite in un ordine prestabilito.  
  
7.  Utilizzare le regole tenendo conto di altre alternative. Ad esempio, se si desidera aggiornare una proprietà quando viene modificato un valore, utilizzare una proprietà calcolata. Se si desidera vincolare le dimensioni o il percorso di una forma, utilizzare un `BoundsRule`. Se si desidera rispondere a una modifica nel valore della proprietà, aggiungere un `OnValueChanged` gestore per la proprietà. Per altre informazioni, vedere [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).  
  
## Esempio  
 Nell'esempio seguente aggiorna una proprietà quando viene creata un'istanza di una relazione di dominio per collegare due elementi. Verrà attivata la regola non solo quando l'utente crea un collegamento in un diagramma, ma anche se il codice del programma crea un collegamento.  
  
 Per testare questo esempio, creare un linguaggio DSL utilizzando il modello di soluzione flusso attività, inserire il codice seguente in un file nel progetto Dsl. Compilare ed eseguire la soluzione e aprire il file di esempio nel progetto di debug. Creare un collegamento commento tra una forma di commento e un elemento del flusso. Report sull'elemento più recente è stata connessa a modifiche del testo del commento.  
  
 In pratica, si scriverebbe in genere un DeleteRule per ogni AddRule.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.TaskRuleExample  
{  
  
  [RuleOn(typeof(CommentReferencesSubjects))]  
  public class RoleRule : AddRule  
  {  
  
    public override void ElementAdded(ElementAddedEventArgs e)  
    {  
      base.ElementAdded(e);  
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;  
      Comment comment = link.Comment;  
      FlowElement subject = link.Subject;  
      Transaction current = link.Store.TransactionManager.CurrentTransaction;  
      // Don't want to run when we're just loading from file:  
      if (current.IsSerializing) return;  
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";  
    }  
  
  }  
  
  public partial class TaskRuleExampleDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(RoleRule));  
      return types.ToArray();  
    }  
  }  
  
}  
  
```  
  
## Vedere anche  
 [I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [Le regole associate \(BoundsRules\) vincolano posizione e dimensione delle forme](../modeling/boundsrules-constrain-shape-location-and-size.md)