---
title: "Personalizzazione del comportamento di eliminazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.deletebehavior"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, eliminazione"
ms.assetid: c6bf088d-52c6-4817-af45-ddae745bb5a9
caps.latest.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 23
---
# Personalizzazione del comportamento di eliminazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'eliminazione di un elemento in genere determina l'eliminazione anche degli elementi correlati.  Tutte le relazioni a esso connesse ed eventuali elementi figlio vengono eliminati.  Questo comportamento è definito *propagazione dell'eliminazione*.  È possibile personalizzare la propagazione dell'eliminazione, ad esempio per fare in modo che vengano eliminati altri elementi correlati.  Scrivendo codice programma, è possibile far dipendere la propagazione dell'eliminazione dallo stato del modello.  È inoltre possibile fare in modo che un'eliminazione comporti altre modifiche.  
  
 In questo argomento sono incluse le seguenti sezioni:  
  
-   [Comportamento di eliminazione predefinito](#default)  
  
-   [Impostazione dell'opzione di propagazione dell'eliminazione di un ruolo](#property)  
  
-   [Override della chiusura dell'eliminazione](#closure): usare questa tecnica quando l'eliminazione potrebbe determinare anche quella degli elementi adiacenti.  
  
-   [Uso di OnDeleting e OnDeleted](#ondeleting): usare questi metodi quando la risposta potrebbe includere altre azioni come l'aggiornamento di un valore all'interno o all'esterno dell'archivio.  
  
-   [Regole di eliminazione](#rules): usare queste regole per propagare gli aggiornamenti di qualsiasi tipo all'interno dell'archivio, nel caso in cui una modifica potrebbe determinarne altre.  
  
-   [Eventi di eliminazione](#rules): usare gli eventi dell'archivio per propagare gli aggiornamenti all'esterno dell'archivio, ad esempio in altri documenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   [Dividi](#unmerge): usare l'operazione Dividi per annullare l'operazione di unione di un elemento figlio al relativo padre.  
  
##  <a name="default"></a> Comportamento di eliminazione predefinito  
 Per impostazione predefinita, la propagazione dell'eliminazione è controllata dalle regole seguenti:  
  
-   Se si elimina un elemento, vengono eliminati anche tutti gli elementi incorporati.  Gli elementi incorporati sono quelli che costituiscono le destinazioni delle relazioni di incorporamento per le quali tali elementi rappresentano l'origine.  Ad esempio, se è presente una relazione di incorporamento da Album a Brano, quando viene eliminato un album specifico, vengono eliminati anche tutti i relativi brani.  
  
     L'eliminazione di un brano, invece, non causa l'eliminazione dell'album.  
  
-   Per impostazione predefinita, l'eliminazione non si propaga lungo le relazioni di riferimento.  Se esiste una relazione di riferimento ArtistPlaysOnAlbum da Album ad Artista, l'eliminazione di un album non determina l'eliminazione dell'artista correlato e l'eliminazione di un artista non determina l'eliminazione di un album.  
  
     Per impostazione predefinita, l'eliminazione si propaga lungo alcune relazioni predefinite.  Ad esempio, quando si elimina un elemento modello, viene eliminata anche la relativa forma sul diagramma.  L'elemento e la forma sono correlati tramite la relazione di riferimento `PresentationViewsSubject`.  
  
-   Ogni relazione connessa all'elemento, sia presso il ruolo di origine o il ruolo di destinazione, viene eliminata.  La proprietà ruolo dell'elemento presso il ruolo opposto non contiene più l'elemento eliminato.  
  
##  <a name="property"></a> Impostazione dell'opzione di propagazione dell'eliminazione di un ruolo  
 È possibile fare in modo che l'eliminazione si propaghi lungo una relazione di riferimento o da un elemento incorporato al relativo padre.  
  
#### Per impostare la propagazione dell'eliminazione  
  
1.  Nel diagramma di definizione DSL selezionare il *ruolo* al quale si vuole propagare l'eliminazione.  Il ruolo è rappresentato dalla linea a sinistra o a destra della casella relativa a una relazione di dominio.  
  
     Ad esempio, per specificare che ogni volta che si elimina un album vengano eliminati anche gli artisti correlati, selezionare il ruolo connesso alla classe di dominio Artista.  
  
2.  Nella finestra Proprietà impostare la proprietà **Propaga eliminazione**.  
  
3.  Premere F5 e verificare che:  
  
    -   Quando si elimina un'istanza della relazione, venga eliminato anche l'elemento presso il ruolo selezionato.  
  
    -   Quando si elimina un elemento presso il ruolo opposto, vengano eliminate anche le istanze della relazione e gli elementi correlati presso tale ruolo.  
  
 L'opzione **Propaga eliminazione** è presente anche nella finestra **Dettagli DSL**.  Selezionare una classe di dominio e aprire la pagina **Comportamento di eliminazione** nella finestra Dettagli DSL facendo clic sul pulsante che si trova sul lato della finestra.  L'opzione **Propaga** è mostrata per il ruolo opposto di ogni relazione.  La colonna **Elimina stile** indica se per l'opzione **Propaga** è usata l'impostazione predefinita, ma non ha alcun effetto separato.  
  
## Propagazione dell'eliminazione usando il codice programma  
 Le opzioni del file di definizione DSL consentono solo di scegliere se propagare l'eliminazione a un elemento immediatamente adiacente.  Per implementare uno schema di propagazione dell'eliminazione più complesso, è possibile scrivere codice programma.  
  
> [!NOTE]
>  Per aggiungere codice programma alla definizione DSL, creare un file di codice separato nel progetto **Dsl** e scrivere definizioni parziali per aumentare le classi nella cartella Codice generato.  Per altre informazioni, vedere [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
##  <a name="closure"></a> Definizione di una chiusura di eliminazione  
 L'operazione di eliminazione usa la classe *Modello***DeleteClosure** per stabilire quali elementi eliminare, data una selezione iniziale.  Chiama `ShouldVisitRelationship()` e `ShouldVisitRolePlayer()` ripetutamente, verificando il grafico delle relazioni.  È possibile eseguire l'override di questi metodi.  ShouldVisitRolePlayer viene fornito con l'identità di un collegamento e l'elemento di uno dei ruoli del collegamento.  Deve restituire uno dei valori seguenti:  
  
-   **VisitorFilterResult.Yes**: l'elemento deve essere eliminato e il walker deve passare a verificare gli altri collegamenti dell'elemento.  
  
-   **VisitorFilterResult.DoNotCare**: l'elemento non deve essere eliminato salvo il caso in cui un'altra query risponda che deve essere eliminato.  
  
-   **VisitorFilterResult.Never**: l'elemento non deve essere eliminato, anche se un'altra query risponde **Yes**, e il walker non deve provare gli altri collegamenti dell'elemento.  
  
```  
// When a musician is deleted, delete their albums with a low rating.  
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs  
partial class MusicLibDeleteClosure  
{  
  public override VisitorFilterResult ShouldVisitRolePlayer  
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,   
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)  
  {  
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;  
    if (link != null   
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)  
    {  
      // Count other unvisited links to the Album of this link.  
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)  
              .Where(linkAlbumArtist =>   
                     linkAlbumArtist != link &&  
                     !walker.Visited(linkAlbumArtist))  
              .Count() == 0)  
      {  
        // Should delete this role player:  
        return VisitorFilterResult.Yes;   
      }  
      else  
        // Don’t delete unless another relationship deletes it:  
        return VisitorFilterResult.DoNotCare;   
    }  
    else   
    {  
      // Test for and respond to other relationships and roles here.  
  
      // Not the relationship or role we’re interested in.  
      return base.ShouldVisitRolePlayer(walker, sourceElement,   
             elementLink, targetDomainRole, targetRolePlayer);  
    }  
  }  
}  
  
```  
  
 La tecnica di chiusura assicura che il set di elementi e collegamenti da eliminare venga stabilito prima dell'avvio dell'eliminazione.  Inoltre, il walker combina i risultati della chiusura con quelli di altre parti del modello.  
  
 Tuttavia, questa tecnica presuppone che l'eliminazione interessi solo gli elementi adiacenti nel grafico delle relazioni: non è possibile usare questo metodo per eliminare un elemento di un'altra parte del modello.  Non è possibile usarlo per aggiungere elementi o effettuare altre modifiche in risposta a un'eliminazione.  
  
##  <a name="ondeleting"></a> Uso di OnDeleting e OnDeleted  
 È possibile eseguire l'override di `OnDeleting()` o di `OnDeleted()` in una classe di dominio o in una relazione di dominio.  
  
1.  <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> viene chiamato quando un elemento sta per essere eliminato, ma prima dello scollegamento delle relative relazioni.  È sempre navigabile da e verso altri elementi e si trova sempre in `store.ElementDirectory`.  
  
     Se si eliminano diversi elementi contemporaneamente, OnDeleting viene chiamato per tutti questi elementi prima di eseguire le eliminazioni.  
  
     `IsDeleting` è true.  
  
2.  <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> è chiamato quando l'elemento è stato eliminato.  Resta nell'heap CLR, quindi è possibile eseguire un'operazione di annullamento, se necessario, ma viene scollegato da altri elementi e rimosso da `store.ElementDirectory`.  Per le relazioni, i ruoli continuano a fare riferimento ai precedenti assegnatari di ruolo.`IsDeleted` è true.  
  
3.  OnDeleting e OnDeleted vengono chiamati quando l'utente richiama l'annullamento dopo aver creato un elemento e quando una precedente eliminazione viene ripetuta nell'operazione di ripristino.  In questi casi, usare `this.Store.InUndoRedoOrRollback` per evitare l'aggiornamento degli elementi dell'archivio.  Per altre informazioni, vedere [Procedura: utilizzare le transazioni per aggiornare il modello](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
 Ad esempio, il codice seguente elimina un album quando l'ultimo brano figlio viene eliminato:  
  
```  
  
// Delete the parent Album when the last Song is deleted.  
// Override methods in the embedding relationship between Album and Song:  
partial class AlbumHasSongs  
{  
  protected override void OnDeleted()  
  {  
    base.OnDeleted();  
    // Don't perform in-store actions in undo:  
    if (this.Store.InUndoRedoOrRollback) return;  
    // Relationship source and target still work:  
    // Don't bother if source is already on its way out:  
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)  
    {  
      if (this.Album.Songs.Count == 0)  
      {   
        this.Album.Delete();  
} } } }  
  
```  
  
 Spesso è più utile attivare l'operazione dall'eliminazione della relazione e non dall'elemento ruolo, perché questa procedura funziona sia quando viene eliminato l'elemento sia quando viene eliminata la relazione stessa.  Tuttavia, per una relazione di riferimento potrebbe essere consigliabile propagare l'eliminazione quando un elemento viene eliminato, ma non quando viene eliminata la relazione stessa.  In questo esempio un album viene eliminato quando si elimina l'ultimo artista, ma se si eliminano le relazioni non si verifica alcuna azione:  
  
```  
using System.Linq; ...  
// Assumes a many-many reference relationship   
// between Artist and Album.    
partial class Artist  
{  
  protected override void OnDeleting()  
  {  
    base.OnDeleting();  
    if (this.Store.InUndoRedoOrRollback) return;  
    List<Album> toDelete = new List<Album>();  
    foreach (Album album in this.Albums)  
    {  
      if (album.Artists.Where(artist => !artist.IsDeleting)  
                        .Count() == 0)  
      {  
        toDelete.Add(album);  
      }  
    }  
    foreach (Album album in toDelete)  
    {  
      album.Delete();  
} } }  
  
```  
  
 Quando si esegue <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> su un elemento, verranno chiamati i metodi OnDeleting e OnDeleted.  Questi metodi vengono sempre eseguiti inline, cioè immediatamente prima e dopo l'eliminazione effettiva.  Se il codice elimina due o più elementi, OnDeleting e OnDeleted verranno chiamati alternativamente su tutti gli elementi.  
  
##  <a name="rules"></a> Regole ed eventi di eliminazione  
 Come alternativa ai gestori OnDelete, è possibile definire regole ed eventi di eliminazione.  
  
1.  Le regole **Deleting** e **Delete** vengono attivate solo in una transazione e non in un'operazione di annullamento o ripristino.  È possibile impostarle in modo che vengano aggiunte a una coda ed eseguite al termine della transazione in cui viene effettuata l'eliminazione.  L'eliminazione delle regole viene sempre eseguita prima di qualsiasi regola di eliminazione presente nella coda.  
  
     Usare le regole per propagare modifiche che influiscono solo sugli elementi dell'archivio, tra cui relazioni, elementi di diagramma e relative proprietà.  In genere una regola Deleting consente di propagare l'eliminazione, mentre una regola Delete consente di creare relazioni ed elementi sostitutivi.  
  
     Per altre informazioni, vedere [Le regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).  
  
2.  L'evento di archivio **Deleted** è richiamato al termine di una transazione e chiamato dopo un'operazione di annullamento o ripristino.  Può essere quindi usato per propagare le eliminazioni di oggetti esterni all'archivio, ad esempio file, voci di database o altri oggetti in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Per altre informazioni, vedere [I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
    > [!WARNING]
    >  Dopo l'eliminazione di un elemento, è possibile accedere ai relativi valori delle proprietà di dominio, ma non è possibile passare ai collegamenti della relazione.  Tuttavia, se si imposta un evento Deleted in una relazione, è possibile anche accedere ai due elementi che ne costituivano gli assegnatari di ruolo.  Quindi, per rispondere all'eliminazione di un elemento modello ma anche accedere a un elemento al quale era collegato, impostare un evento Delete nella relazione invece che nella classe di dominio dell'elemento.  
  
### Esempio di regole di eliminazione  
  
```  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletingRule : DeletingRule  
{  
  public override void ElementDeleting(ElementDeletingEventArgs e)  
  {  
    base.ElementDeleting(e);  
    // ...perform tasks to propagate imminent deletion  
  }  
}  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletedRule : DeleteRule  
{  
  public override void ElementDeleted(ElementDeletedEventArgs e)  
  {  
    base.ElementDeleted(e);  
    // ...perform tasks such as creating new elements  
  }  
}  
  
// The rule must be registered:  
public partial class MusicLibDomainModel  
{  
  protected override Type[] GetCustomDomainModelTypes()  
  {  
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
    types.Add(typeof(AlbumDeletingRule));  
    types.Add(typeof(AlbumDeletedRule));  
    // If you add more rules, list them here.   
    return types.ToArray();  
  }  
}  
  
```  
  
### Esempio di evento Deleted  
  
```  
partial class NestedShapesSampleDocData  
{  
  protected override void OnDocumentLoaded(EventArgs e)  
  {  
    base.OnDocumentLoaded(e);  
    DomainRelationshipInfo commentRelationship =   
          this.Store.DomainDataDirectory  
          .FindDomainRelationship(typeof(CommentsReferenceComponents));  
  
    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,  
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));  
  }  
  
  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)  
  {  
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;  
    Comment comment = link.Comment;  
    Component component = link.Subject;  
    if (comment.IsDeleted)  
    {  
      // The link was deleted because the comment was deleted.  
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);  
    }  
    else  
    {  
      // It was just the link that was deleted - the comment itself remains.  
      System.Windows.Forms.MessageBox.Show("Removed comment link to "   
           + component.Name);  
    }  
  }  
}  
  
```  
  
##  <a name="unmerge"></a> Divisione  
 L'operazione che collega un elemento figlio al padre è definita *unione*.  Si verifica quando un nuovo elemento o gruppi di elementi vengono creati dalla casella degli strumenti o spostati da un'altra parte del modello oppure copiati dagli Appunti.  Oltre a creare una relazione di incorporamento tra l'elemento padre e il nuovo elemento figlio, l'operazione di unione può anche impostare altre relazioni, creare elementi ausiliari e impostare valori di proprietà negli elementi.  L'operazione di unione è incapsulata in una direttiva di unione degli elementi \(EMD\).  
  
 Una EMD incapsula anche l'operazione di *divisione* o `MergeDisconnect` complementare.  Se è presente un cluster di elementi che è stato costruito tramite un'operazione di unione, per rimuovere un elemento dal cluster è consigliabile usare l'operazione di divisione associata, nel caso in cui si voglia mantenere la coerenza dello stato degli elementi rimanenti.  Per l'operazione di divisione vengono usate in genere le tecniche descritte nelle sezioni precedenti.  
  
 Per altre informazioni, vedere [Personalizzazione della creazione e dello spostamento di elementi](../modeling/customizing-element-creation-and-movement.md).  
  
## Vedere anche  
 [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)   
 [Personalizzazione della creazione e dello spostamento di elementi](../modeling/customizing-element-creation-and-movement.md)   
 [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)