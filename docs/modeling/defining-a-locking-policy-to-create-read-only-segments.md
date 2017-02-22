---
title: "Definizione di un criterio di blocco per creare segmenti di sola lettura | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 12
caps.handback.revision: 12
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Definizione di un criterio di blocco per creare segmenti di sola lettura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Immutabilità API di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] L'sdk di visualizzazione e modellazione concede un programma alla parte del blocco o qualsiasi modello \(DSL\) di linguaggio specifico di dominio in modo da poter essere letto ma non modificare.  Questa opzione di sola lettura può essere utilizzata, ad esempio, in modo che un utente può chiedere ai colleghi di annotare e rivedere un modello DSL ma può impedirne la modifica originale.  
  
 Inoltre, l'autore di un linguaggio specifico di dominio, è possibile definire un oggetto *criteri del blocco.* I criteri di blocco vengono definiti i blocchi sono consentiti, non valido, o obbligatorio.  Ad esempio, quando si pubblica un linguaggio specifico di dominio, è possibile favorire gli sviluppatori di terze parti a estenderla con i nuovi controlli.  È tuttavia anche possibile utilizzare i criteri di blocco per impedire la modifica dello stato di sola lettura delle parti specifiche del modello.  
  
> [!NOTE]
>  I criteri del blocco possono essere aggirati tramite reflection.  Fornisce un semplice limite per gli sviluppatori di terze parti, ma non fornisce una forte sicurezza.  
  
 Ulteriori informazioni ed esempi disponibili per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [L'sdk di visualizzazione e modellazione](http://go.microsoft.com/fwlink/?LinkId=186128) sito Web.  
  
## Impostazione e recupero dei blocchi  
 È possibile impostare impostate l'archivio, una partizione, o su un elemento.  Ad esempio, questa istruzione di un elemento del modello da eliminare e anche se le relative proprietà venga modificato:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Altri valori di blocco possono essere utilizzati per impedire le modifiche delle relazioni, la creazione dell'elemento, spostarsi tra le partizioni e la riordinazione di collegamenti in un ruolo.  
  
 I blocchi vengono applicate sia alle azioni utente che nel codice del programma.  Se il codice del programma tenta di apportare una modifica, `InvalidOperationException` verrà generato.  I blocchi vengono ignorati in un'operazione di annullamento o ripristino.  
  
 È possibile individuare se un elemento presenta un qualsiasi blocco in un dato insieme tramite `IsLocked(Locks)` ed è possibile ottenere l'impostazione corrente di impostare un elemento tramite  `GetLocks()`.  
  
 È possibile impostare un blocco senza utilizzare una transazione.  Il database del blocco non fa parte dell'archivio.  Se si imposta un blocco in risposta a una modifica di un valore nell'archivio, ad esempio in OnValueChanged, si consente le modifiche che fanno parte di un'operazione di annullamento.  
  
 Questi metodi sono metodi di estensione definiti in <xref:Microsoft.VisualStudio.Modeling.Immutability> spazio dei nomi.  
  
### Imposta le partizioni e gli archivi  
 I blocchi possono essere applicati anche alle partizioni e all'archivio.  Un blocco viene impostato su una partizione è applicabile a tutti gli elementi della partizione.  Di conseguenza, ad esempio, la seguente istruzione " tutti gli elementi in una partizione venga eliminato, indipendentemente dagli stati dei rispettivi blocchi.  tuttavia, altri blocchi come `Locks.Property` può ancora essere impostato sui singoli elementi:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Un blocco viene impostato riguardanti l'archivio viene applicata a tutti i relativi elementi, indipendentemente dalle impostazioni di che imposta le partizioni gli elementi e.  
  
### Utilizzo dei blocchi  
 È possibile utilizzare i blocchi per implementare le combinazioni quali ad esempio:  
  
-   Per impedire le modifiche a tutti gli elementi e le relazioni ad eccezione di quelli che rappresentano i commenti.  In questo modo gli utenti annotino un modello senza modificarlo.  
  
-   Per impedire le modifiche della partizione predefinita, ma sono consentite modifiche della partizione del diagramma.  È possibile ridisporre il diagramma, ma non può alterare il modello sottostante.  
  
-   Per impedire le modifiche all'archivio ad eccezione di un gruppo di utenti registrati in un database separato.  Per altri utenti, il diagramma e il modello sono di sola lettura.  
  
-   Per impedire le modifiche al modello se una proprietà booleana del diagramma è impostata su true.  Fornire un comando di menu modificare tale proprietà.  Ciò consente di garantire gli utenti che non passano a modifiche accidentalmente.  
  
-   Per impedire l'aggiunta e l'eliminazione degli elementi e le relazioni delle classi specifiche, ma sono consentite modifiche della proprietà.  Ciò fornisce agli utenti con un di stampo fissa in cui è possibile riempire le proprietà.  
  
## Valori di blocco  
 I blocchi possono essere impostati in un archivio, una partizione, o su un utente ModelElement.  I blocchi è un oggetto `Flags` enumerazione: è possibile combinare i relativi valori utilizzando “&#124;„.  
  
-   I blocchi di ModelElement includono sempre i blocchi della partizione.  
  
-   I blocchi di partizione includono sempre i blocchi dell'archivio.  
  
 Non è possibile impostare un blocco su una partizione o archiviare e contemporaneamente disabilitare il blocco da un singolo elemento.  
  
|Valore|Indicare se `IsLocked(Value)` è true|  
|------------|------------------------------------------|  
|Nessuno|nessuna restrizione.|  
|Proprietà|Le proprietà del dominio dell'elemento non possono essere modificate.  Ciò non si applica alle proprietà che vengono generate dal ruolo di una classe di dominio in una relazione.|  
|Add|i nuovi elementi e collegamenti non possono essere creati in una partizione o in un archivio.<br /><br /> non applicabile a `ModelElement`.|  
|Spostamento|L'elemento non può essere spostato tra le partizioni se `element.IsLocked(Move)` è true, o se  `targetPartition.IsLocked(Move)` è true.|  
|Delete|Un elemento non può essere eliminato se questo blocco è impostato sull'elemento stesso, o in uno qualsiasi degli elementi a cui l'eliminazione è propagherebbe, ad esempio gli elementi incorporati e forme.<br /><br /> È possibile utilizzare `element.CanDelete()` per individuare se un elemento può essere eliminato.|  
|Riordina|L'ordine dei collegamenti in un roleplayer non può essere modificato.|  
|RolePlayer|Il set di collegamenti che sono originati a questo elemento non può essere modificato.  Ad esempio, i nuovi elementi non possono essere incorporati in questo elemento.  Ciò non influisce sui collegamenti per il quale questo elemento sia il database di destinazione.<br /><br /> Se l'elemento è un collegamento, né l'origine e la destinazione non vengono influenzate.|  
|Tutte|OR bit per bit degli altri valori.|  
  
## Criteri di blocco  
 L'autore di un linguaggio specifico di dominio, è possibile definire un oggetto *criteri di blocco*.  I criteri di blocco moderano l'operazione di SetLocks\(\), in modo che sia possibile impedire che i blocchi specifici venga impostato o lasciare che in vi sono i blocchi specifici devono essere impostati.  In genere, si utilizza i criteri di blocco per scoraggiare gli utenti e gli sviluppatori accidentalmente dalla contestazione dell'utilizzo previsto di un linguaggio specifico di dominio, allo stesso modo in cui è possibile dichiarare una variabile `private`.  
  
 È inoltre possibile utilizzare i criteri di blocco per impostare impostate tutti gli elementi dipendenti dal tipo di elemento.  Ciò è dovuto `SetLocks(Locks.None)` viene sempre chiamato quando un elemento viene creato o deserializzato dal file.  
  
 Tuttavia, non è possibile utilizzare i criteri per variare impostate un elemento per tutta la sua vita.  Per raggiungere tale fenomeno, è consigliabile utilizzare le chiamate a `SetLocks()`.  
  
 Per definire i criteri di blocco, è necessario:  
  
-   Creare una classe che implementa <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.  
  
-   Aggiungere la classe ai servizi disponibili con il DocData del linguaggio DSL.  
  
### Per definire i criteri di blocco  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> con la seguente definizione:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Questi metodi vengono chiamati quando viene effettuata una chiamata a `SetLocks()` in un archivio, una partizione, o in un ModelElement.  In ogni metodo, viene fornito un set di proposto di blocchi.  È possibile restituire il set proposto alternativa, è possibile aggiungere e ridurre i blocchi.  
  
 Di seguito è riportato un esempio:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{  
  public class MyLockingPolicy : ILockingPolicy  
  {  
    /// <summary>  
    /// Moderate SetLocks(this ModelElement target, Locks locks)  
    /// </summary>  
    /// <param name="element">target</param>  
    /// <param name="proposedLocks">locks</param>  
    /// <returns></returns>  
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)  
    {  
      // In my policy, users can never delete an element,  
      // and other developers cannot easily change that:  
      return proposedLocks | Locks.Delete);  
    }  
    public Locks RefineLocks(Store store, Locks proposedLocks)  
    {  
      // Only one user can change this model:  
      return Environment.UserName == "aUser"   
           ? proposedLocks : Locks.All;  
    }  
  
```  
  
 Per garantire che gli utenti possano rimuovere sempre gli elementi, anche se altre chiamate di codice `SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Per impedire modifica in tutte le proprietà di ogni elemento MyClass:  
  
 `return element is MyClass ?  (proposedLocks | Locks.Property) : proposedLocks;`  
  
### Per rendere i criteri come servizio  
 in `DslPackage` il progetto, aggiungere un nuovo file contenente il codice analogo al seguente:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{   
  // Override the DocData GetService() for this DSL.  
  internal partial class YourDslDocData // Change  
  {  
    /// <summary>  
    /// Custom locking policy cache.  
    /// </summary>  
    private ILockingPolicy myLockingPolicy = null;  
  
    /// <summary>  
    /// Called when a service is requested.  
    /// </summary>  
    /// <param name="serviceType">Service requested</param>  
    /// <returns>Service implementation</returns>  
    public override object GetService(System.Type serviceType)  
    {  
      if (serviceType == typeof(SLockingPolicy)   
       || serviceType == typeof(ILockingPolicy))  
      {  
        if (myLockingPolicy == null)  
        {  
          myLockingPolicy = new MyLockingPolicy();  
        }  
        return myLockingPolicy;  
      }  
      // Request is for some other service.  
      return base.GetService(serviceType);  
    }  
}  
```