---
title: "I gestori eventi propagano le modifiche al di fuori del modello | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, eventi"
  - "Linguaggio specifico di dominio, programmazione di modelli di dominio"
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: 18
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 18
---
# I gestori eventi propagano le modifiche al di fuori del modello
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nell'SDK di visualizzazione e modellazione di, è possibile definire i gestori eventi dell'archivio per propagare le modifiche alle risorse all'esterno dell'archivio, ad esempio variabili non archivio, i file, i modelli in altri archivi, o altro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensioni.  I gestori eventi dell'archivio vengono eseguite dopo la fine della transazione nella quale evento scatenante si è verificato.  Vengono eseguiti in un'operazione di annullamento o ripristino.  Di conseguenza, a differenza delle regole di archiviazione, gli eventi dell'archivio sono particolarmente utili per aggiornare i valori al di fuori dell'archivio.  A differenza degli eventi di .NET, i gestori eventi dell'archivio vengono registrati per ascoltare classe: non è necessario registrare un gestore distinto per ogni istanza.  Per ulteriori informazioni su come scegliere tra diversi modi per gestire le modifiche, vedere [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).  
  
 L'area grafica e altri controlli dell'interfaccia utente sono esempi di risorse esterne che possono essere gestite dagli eventi dell'archivio.  
  
### Per definire un evento dell'archivio  
  
1.  Scegliere il tipo di evento che si desidera monitorare.  Per un elenco completo, esaminare le proprietà di <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>.  Ogni proprietà corrisponde a un tipo di evento.  Il più delle volte tipi di evento utilizzati sono:  
  
    -   `ElementAdded` \- attivato quando un elemento del modello, un collegamento di relazione, una forma o un connettore viene creato.  
  
    -   ElementPropertyChanged \- attivato se il valore di un oggetto `Normal` la proprietà del dominio viene modificata.  L'evento viene attivato solo se i valori nuovi e precedenti non sono uguali.  L'evento non può essere applicato alle proprietà uguali e personalizzate di archiviazione.  
  
         Impossibile applicare al ruolo delle proprietà che corrispondono ai collegamenti della relazione.  Utilizzare, invece `ElementAdded` per monitorare la relazione di dominio.  
  
    -   `ElementDeleted` \- attivato dopo un elemento del modello, una relazione, una forma o un connettore è stato eliminato.  È ancora possibile accedere ai valori della proprietà dell'elemento, ma non disporrà di relazioni con altri elementi.  
  
2.  aggiungere una definizione di classe parziale per *TheDsl***DocData** in un file di codice distinto in  **DslPackage** progetto.  
  
3.  Scrivere il codice dell'evento come metodo, come nell'esempio seguente.  può essere `static`, a meno che non si desideri accedere a  `DocData`.  
  
4.  override `OnDocumentLoaded()` per registrare il gestore.  Se si dispone di più di un gestore, è possibile usufruire di tutti nella stessa posizione.  
  
 La posizione del codice di registrazione non è essenziale.  `DocView.LoadView()` è un percorso alternativo.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.MusicLib  
{  
  partial class MusicLibDocData  
  {  
    // Register store events here or in DocView.LoadView().  
    protected override void OnDocumentLoaded()  
    {  
      base.OnDocumentLoaded(); // Don’t forget this.  
  
      #region Store event handler registration.       
      Store store = this.Store;  
      EventManagerDirectory emd = store.EventManagerDirectory;  
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory  
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));  
      emd.ElementAdded.Add(linkInfo,   
          new EventHandler<ElementAddedEventArgs>(AddLink));  
      emd.ElementDeleted.Add(linkInfo,   
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));  
  
      #endregion Store event handlers.  
    }  
  
    private void AddLink(object sender, ElementAddedEventArgs e)  
    {  
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;  
      if (link != null)   
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);  
    }  
    private void RemoveLink(object sender, ElementDeletedEventArgs e)  
    {  
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;  
      if (link != null)   
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);  
    }  
  }  
  
}  
  
```  
  
## Utilizzando gli eventi per apportare regolazioni annullabile nell'archivio  
 Gli eventi dell'archivio generalmente non sono utilizzati per la propagazione delle modifiche nell'archivio, poiché il gestore eventi viene eseguito dopo che la transazione viene eseguito il commit.  Al contrario, si utilizzerebbe una regola dell'archivio.  Per ulteriori informazioni, vedere [Le regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Tuttavia, è possibile utilizzare in un gestore eventi per eseguire aggiornamenti aggiuntivi all'archivio, se si desidera che l'utente possa annullare separatamente gli aggiornamenti aggiuntivi dall'evento originale.  Ad esempio, si supponga che i caratteri minuscoli vengano la convenzione utilizzata in genere per i titoli dell'album.  È possibile scrivere un gestore eventi dell'archivio che corregge il titolo in minuscolo dopo che l'utente ha immesso in lettere maiuscole.  Ma è possibile utilizzare il comando annulla per annullare la correzione, il ripristino dei caratteri maiuscoli.  Una seconda annulla rimuoverebbe la modifica dell'utente.  
  
 Al contrario, se si scrivessero una regola di eseguire la stessa operazione, la modifica dell'utente e la correzione verrebbe nella stessa transazione, in modo che l'utente non può annullare la modifica senza perdere la modifica originale.  
  
```  
  
partial class MusicLibDocView  
{  
    // Register store events here or in DocData.OnDocumentLoaded().  
    protected override void LoadView()  
    {  
      /* Register store event handler for Album Title property. */  
      // Get reflection data for property:  
      DomainPropertyInfo propertyInfo =   
        this.DocData.Store.DomainDataDirectory  
        .FindDomainProperty(Album.TitleDomainPropertyId);  
      // Add to property handler list:  
      this.DocData.Store.EventManagerDirectory  
        .ElementPropertyChanged.Add(propertyInfo,  
        new EventHandler<ElementPropertyChangedEventArgs>  
             (AlbumTitleAdjuster));  
  
      /*  
      // Alternatively, you can set one handler for   
      // all properties of a class.  
      // Your handler has to determine which property changed.  
      DomainClassInfo classInfo = this.Store.DomainDataDirectory  
           .FindDomainClass(typeof(Album));  
      this.Store.EventManagerDirectory  
          .ElementPropertyChanged.Add(classInfo,  
        new EventHandler<ElementPropertyChangedEventArgs>  
             (AlbumTitleAdjuster));  
       */  
      return base.LoadView();  
    }  
  
// Undoable adjustment after a property is changed.   
// Method can be static since no local access.  
private static void AlbumTitleAdjuster(object sender,  
         ElementPropertyChangedEventArgs e)  
{  
  Album album = e.ModelElement as Album;  
  Store store = album.Store;  
  
  // We mustn't update the store in an Undo:  
  if (store.InUndoRedoOrRollback   
      || store.InSerializationTransaction)  
      return;  
  
  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)  
  {  
    string newValue = (string)e.NewValue;  
    string lowerCase = newValue.ToLowerInvariant();  
    if (!newValue.Equals(lowerCase))  
    {  
      using (Transaction t = store.TransactionManager  
            .BeginTransaction("adjust album title"))  
      {  
        album.Title = lowerCase;  
        t.Commit();  
      } // Beware! This could trigger the event again.  
    }  
  }  
  // else other properties of this class.  
}  
  
```  
  
 Se si scrive un evento che aggiorna l'archivio:  
  
-   utilizzo `store.InUndoRedoOrRollback` per evitare apportare modifiche agli elementi del modello di annullamento.  Il gestore delle transazioni imposterà un archivio di nuovo allo stato originale.  
  
-   utilizzo `store.InSerializationTransaction` per evitare apportare modifiche mentre il modello viene caricato dal file.  
  
-   Le modifiche causano l'aggiornamento di ulteriori eventi a essere attivate.  Assicurarsi di evitare un ciclo infinito.  
  
## Tipi di eventi dell'archivio  
 Ogni tipo di evento corrisponde a una raccolta in Store.EventManagerDirectory.  È possibile aggiungere o rimuovere i gestori eventi in qualsiasi momento, ma è solito aggiungerli quando il documento viene caricato.  
  
|`EventManagerDirectory` nome proprietà|eseguito quando|  
|--------------------------------------------|---------------------|  
|ElementAdded|Un'istanza di una classe di dominio, una relazione di dominio, una forma, un connettore o di un diagramma viene creata.|  
|ElementDeleted|Un elemento del modello è stato rimosso dalla directory dell'elemento dell'archivio e non è più l'origine o la destinazione di una relazione.  L'elemento non viene eliminato dalla memoria, ma viene mantenuto nel caso di un'operazione di annullamento futura.|  
|ElementEventsBegun|Richiamato alla fine di una transazione esterna.|  
|ElementEventsEnded|richiamato quando tutti gli altri eventi sono stati elaborati.|  
|ElementMoved|Un elemento del modello è stato spostato da una partizione dell'archivio a un altro.<br /><br /> Questa operazione non è correlata alla posizione di una forma sul diagramma.|  
|ElementPropertyChanged|Il valore di una proprietà del dominio è stato modificato.  Questa operazione viene eseguita solo se i valori nuovi e precedenti sono diversi.|  
|RolePlayerChanged|Uno dei due ruoli \(estremità\) di una relazione fa riferimento un nuovo elemento.|  
|RolePlayerOrderChanged|In un ruolo con molteplicità maggiore di 1, la sequenza di plug\-in è stato modificato.|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## Vedere anche  
 [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)   
 [codice di esempio: schemi circuitali](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)