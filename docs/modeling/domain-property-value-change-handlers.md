---
title: "Gestori di modifica del valore delle propriet&#224; del dominio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, esecuzione di override sui gestori di eventi."
ms.assetid: 96d8f392-045e-4bc5-b165-fbaa470a3e16
caps.latest.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 24
---
# Gestori di modifica del valore delle propriet&#224; del dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In un linguaggio specifico di dominio di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], quando il valore di una proprietà di dominio cambia, i metodi `OnValueChanging()` e `OnValueChanged()` vengono richiamati nel gestore delle proprietà di dominio.  Per rispondere alla modifica, è possibile eseguire l'override di tali metodi.  
  
## Override dei metodi del gestore delle proprietà  
 Ogni proprietà di dominio del linguaggio specifico di dominio è gestita da una classe annidata nella propria classe di dominio padre.  Il nome segue il formato *NomeProprietà*GestoreProprietà.  È possibile esaminare questa classe del gestore delle proprietà nel file **Dsl\\Generated Code\\DomainClasses.cs**.  Nella classe `OnValueChanging()` viene chiamato immediatamente prima che il valore cambi, mentre `OnValueChanged()` immediatamente dopo.  
  
 Si supponga ad esempio di avere una classe di dominio `Comment` con una proprietà di dominio stringa denominata `Text` e una proprietà Integer denominata `TextLengthCount`.  Per fare in modo che `TextLengthCount` contenga sempre la lunghezza della stringa `Text`, si potrebbe scrivere il codice seguente in un file separato nel progetto Dsl:  
  
```  
// Domain Class "Comment":  
public partial class Comment   
{  
  // Domain Property "Text":  
  partial class TextPropertyHandler  
  {  
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)  
    {  
      base.OnValueChanging(element, oldValue, newValue);  
  
      // To update values outside the Store, write code here.  
  
      // Let the transaction manager handle undo:  
      Store store = element.Store;  
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;  
  
      // Update values in the Store:  
      this.TextLengthCount = newValue.Length;  
    }  
  }  
}  
  
```  
  
 Notare gli aspetti seguenti sui gestori delle proprietà:  
  
-   I metodi del gestore delle proprietà vengono chiamati sia quando l'utente apporta modifiche a una proprietà di dominio che quando il codice programma assegna un valore diverso alla proprietà.  
  
-   I metodi vengono chiamati solo quando il valore viene effettivamente modificato.  Il gestore non viene richiamato se il codice programma assegna un valore uguale al valore corrente.  
  
-   Le proprietà calcolate e personalizzate del dominio di storage non dispongono di metodi OnValueChanged e OnValueChanging.  
  
-   Non è possibile usare un gestore delle modifiche per modificare il nuovo valore.  Per eseguire questa operazione, ad esempio al fine di limitare il valore a un intervallo specifico, definire un `ChangeRule`.  
  
-   Non è possibile aggiungere un gestore delle modifiche a una proprietà che rappresenta un ruolo di una relazione.  Definire invece un elemento `AddRule` e un elemento `DeleteRule` sulla classe relazione.  Queste regole vengono attivate quando i collegamenti vengono creati o modificati.  Per altre informazioni, vedere [Le regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).  
  
### Modifiche all'interno e all'esterno dell'archivio  
 I metodi del gestore delle proprietà vengono chiamati all'interno della transazione che ha iniziato la modifica.  È quindi possibile apportare altre modifiche all'archivio senza aprire una nuova transazione.  Le modifiche potrebbero determinare altre chiamate del gestore.  
  
 Quando una transazione viene annullata, riapplicata o ne viene eseguito il rollback, non devono essere operate modifiche nell'archivio, ossia modifiche a elementi di modello, relazioni, forme, connettori, diagrammi o alle relative proprietà.  
  
 Inoltre, i valori non vanno in genere aggiornati quando il modello viene caricato da file.  
  
 Le modifiche al modello devono quindi essere verificate da un test come il seguente:  
  
```  
if (!store.InUndoRedoOrRollback   
         && !store. InSerializationTransaction)  
{ this.TextLength = ...; // in-store changes   
}  
```  
  
 D'altra parte, se il gestore delle proprietà propaga le modifiche all'esterno dell'archivio, ad esempio in un file, in un database o in una variabile non di archivio, è necessario operare sempre tali modifiche in modo tale che i valori esterni vengano aggiornati quando l'utente richiama l'annullamento o il ripristino.  
  
### Annullamento di una modifica  
 Se si vuole impedire una modifica, è possibile eseguire il rollback dell'ultima transazione.  Si potrebbe ad esempio fare in modo che una proprietà resti compresa all'interno di un intervallo specifico.  
  
```  
if (newValue > 10)   
{ store.TransactionManager.CurrentTransaction.Rollback();  
  System.Windows.Forms.MessageBox.Show("Value must be less than 10");  
}  
  
```  
  
### Tecnica alternativa: proprietà calcolate  
 Nell'esempio precedente viene illustrato come usare OnValueChanged\(\) per propagare valori da una proprietà di dominio a un'altra.  Ogni proprietà presenta il proprio valore archiviato.  
  
 In alternativa, si potrebbe definire la proprietà derivata come proprietà calcolata.  In questo caso la proprietà non dispone di archiviazione propria e la sua funzione di definizione viene valutata ogni volta che è necessario il relativo valore.  Per altre informazioni, vedere [Proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md).  
  
 Anziché procedere come nell'esempio precedente, è possibile impostare il campo **Kind** di `TextLengthCount` per essere **calcolato** nella definizione DSL.  Per questa proprietà di dominio è necessario fornire il proprio metodo **Get**.  Il metodo **Get** restituirà la lunghezza attuale della stringa di `testo`.  
  
 Un potenziale svantaggio dell'uso di proprietà calcolate, tuttavia, è il fatto che l'espressione viene valutata ogni volta che viene usato il valore, il che potrebbe dare luogo a problemi di prestazioni.  In una proprietà calcolata, inoltre, non sono presenti elementi OnValueChanging\(\) e OnValueChanged\(\).  
  
### Tecnica alternativa: elementi ChangeRule  
 Se si definisce una regola ChangeRule, questa verrà eseguita al termine di una transazione in cui il valore di una proprietà viene modificato.  Per altre informazioni, vedere [Le regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Se in una transazione sono presenti numerose modifiche, la regola ChangeRule verrà eseguita dopo che queste sono state tutte applicate.  I metodi OnValue...  vengono invece eseguiti quando alcune delle modifiche non sono state completate.  A seconda del risultato che si intende raggiungere, la scelta di una regola ChangeRule potrebbe risultare più appropriata.  
  
 È anche possibile usare una regola ChangeRule per regolare il nuovo valore della proprietà per contenerlo entro un intervallo specificato.  
  
> [!WARNING]
>  Se una regola opera modifiche al contenuto dell'archivio, potrebbe verificarsi l'attivazione di altre regole e gestori delle proprietà.  Se una regola modifica la proprietà che ne ha determinato l'attivazione, verrà chiamata nuovamente.  È necessario assicurarsi che le definizioni delle regole non risultino in attivazioni senza termine.  
  
```  
using Microsoft.VisualStudio.Modeling;   
...  
// Change rule on the domain class Comment:  
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]   
class MyCommentTrimRule : ChangeRule  
{  
  public override void   
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
  {  
    base.ElementPropertyChanged(e);  
    Comment comment = e.ModelElement as Comment;  
  
    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))  
      comment.Text = comment.Text.Trim();  
    // If changed, rule will trigger again.  
  }  
}  
  
// Register the rule:   
public partial class MyDomainModel   
{  
 protected override Type[] GetCustomDomainModelTypes()   
 { return new Type[] { typeof(MyCommentTrimRule) };   
 }  
}  
  
```  
  
## Esempio  
  
### Descrizione  
 Nell'esempio seguente viene eseguito l'override del gestore delle proprietà di una proprietà di dominio e viene inviata notifica all'utente quando una proprietà per la classe di dominio `ExampleElement` viene modificata.  
  
### Codice  
  
```  
using DslModeling = global::Microsoft.VisualStudio.Modeling;  
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;  
  
namespace msft.FieldChangeSample  
{  
  public partial class ExampleElement  
  {  
    internal sealed partial class NamePropertyHandler  
    {  
      protected override void OnValueChanged(ExampleElement element,  
         string oldValue, string newValue)  
      {  
        if (!this.Store.InUndoRedoOrRollback)  
        {  
           // make in-store changes here...  
        }  
        // This part is called even in undo:  
        System.Windows.Forms.MessageBox.Show("Value Has Changed");  
        base.OnValueChanged(element, oldValue, newValue);  
      }  
    }  
  }  
}  
```  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Modeling.DomainPropertyValueHandler%602.OnValueChanged%2A>   
 <xref:Microsoft.VisualStudio.Modeling.DomainPropertyValueHandler%602.OnValueChanging%2A>