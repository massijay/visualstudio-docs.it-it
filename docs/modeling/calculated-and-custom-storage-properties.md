---
title: "Propriet&#224; di archiviazione calcolate e personalizzate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, le proprietà del dominio di programmazione"
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 19
---
# Propriet&#224; di archiviazione calcolate e personalizzate
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Tutte le proprietà di dominio in un linguaggio specifico di dominio \(DSL\) possono essere visualizzate all'utente nel diagramma e in Esplora linguaggio ed sono accessibile dal codice programma. Tuttavia, le proprietà variano in modo che i valori vengono archiviati.  
  
## Tipi di proprietà di dominio  
 Nella definizione DSL, è possibile impostare il **tipo** di una proprietà di dominio, come elencato nella tabella riportata di seguito:  
  
|Tipo di proprietà di dominio|Descrizione|  
|----------------------------------|-----------------|  
|**Standard** \(predefinito\)|Una proprietà di dominio che viene salvata nel *archiviare* e serializzati in file.|  
|**Calcolata**|Una proprietà di dominio di sola lettura che non viene salvata nell'archivio, ma viene calcolata da altri valori.<br /><br /> Ad esempio, `Person.Age` può essere calcolato da `Person.BirthDate`.<br /><br /> È necessario fornire il codice che esegue il calcolo. In genere, il calcolo del valore da altre proprietà di dominio. Tuttavia, è possibile utilizzare anche le risorse esterne.|  
|**Archiviazione personalizzati**|Proprietà del dominio che non viene salvata direttamente nell'archivio, ma può essere sia get che set.<br /><br /> È necessario fornire i metodi get e set il valore.<br /><br /> Ad esempio, `Person.FullAddress` possono essere archiviati in `Person.StreetAddress`, `Person.City`, e `Person.PostalCode`.<br /><br /> È inoltre possibile accedere a risorse esterne, ad esempio per ottenere e impostare i valori da un database.<br /><br /> Il codice non necessario impostare i valori nell'archivio quando `Store.InUndoRedoOrRollback` è true. Vedere [transazioni e setter personalizzato](#setters).|  
  
## Fornire il codice per una proprietà calcolata o personalizzato di archiviazione  
 Se si imposta il tipo della proprietà del dominio calcolata o di archiviazione personalizzati, è necessario fornire metodi di accesso. Quando si compila la soluzione, un report di errore indicherà che cosa è necessario.  
  
#### Per definire un valore calcolato o una proprietà di archiviazione personalizzati  
  
1.  Selezionare la proprietà di dominio nel diagramma o in Dsldefinition, **Esplora DSL**.  
  
2.  Nel **proprietà** finestra, impostare il **tipo** campo **calcolato** o **archiviazione personalizzata**.  
  
     Assicurarsi di avere impostato anche il relativo **tipo** nel modo desiderato.  
  
3.  Fare clic su **Trasforma tutti i modelli** sulla barra degli strumenti di **Esplora**.  
  
4.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
     Viene visualizzato il messaggio di errore seguente: "*ClasseUtente* non contiene una definizione per Get*YourProperty*."  
  
5.  Fare doppio clic sul messaggio di errore.  
  
     Si apre Dsl\\GeneratedCode\\DomainClasses.cs o DomainRelationships.cs. Sopra la chiamata al metodo evidenziato, un commento viene richiesto di fornire un'implementazione per Get*YourProperty*\(\).  
  
    > [!NOTE]
    >  Questo file viene generato da Dsldefinition. Se si modifica il file, le modifiche andranno perse la volta successiva che si fa clic su **Trasforma tutti i modelli**. Aggiungere il metodo richiesto in un file separato.  
  
6.  Creare o aprire un file di classe in una cartella separata, ad esempio CustomCode\\*YourDomainClass*. cs.  
  
     Assicurarsi che lo spazio dei nomi è uguale a quello del codice generato.  
  
7.  Nel file di classe, scrivere un'implementazione parziale della classe di dominio. Nella classe, scrivere una definizione di parametro mancante `Get` metodo che è simile all'esempio seguente:  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  Se si imposta **tipo** a **archiviazione personalizzata**, sarà inoltre necessario fornire un `Set` metodo. Ad esempio:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     Il codice non necessario impostare i valori nell'archivio quando `Store.InUndoRedoOrRollback` è true. Vedere [transazioni e setter personalizzato](#setters).  
  
9. Compilare ed eseguire la soluzione.  
  
10. Verificare la proprietà. Assicurarsi che si tenta **Annulla** e **Ripeti**.  
  
##  <a name="setters"></a> Le transazioni e setter personalizzato  
 Nel metodo Set di proprietà di archiviazione personalizzati, non è necessario aprire una transazione, perché in genere viene chiamato il metodo all'interno di una transazione attiva.  
  
 Tuttavia, il metodo Set potrebbe anche chiamato se l'utente richiama l'annullamento o ripristino oppure se una transazione è in fase di rollback. Quando <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> è true, il metodo Set deve comportarsi come indicato di seguito:  
  
-   Consigliabile non apportare modifiche nell'archivio, ad esempio l'assegnazione di valori di altre proprietà di dominio. La gestione degli annullamenti imposterà i relativi valori.  
  
-   Tuttavia, è necessario aggiornare eventuali risorse esterne, ad esempio database o il contenuto del file o oggetti all'esterno dell'archivio. Questo garantirà che si trovano in synchronism con i valori nell'archivio.  
  
 Ad esempio:  
  
```  
void SetAgeValue(int value)  
{   
  // If we are in Undo, no changes to Store objects:  
  if (!this.Store.InUndoRedoOrRollback)  
  {   
    this.BirthYear = System.DateTime.Today.Year - value;   
  }  
  // But always update external objects:  
  System.IO.File.WriteAllText(AgeFile, value);  
}  
```  
  
 Per ulteriori informazioni sulle transazioni, vedere [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## Vedere anche  
 [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Proprietà delle proprietà di dominio](../modeling/properties-of-domain-properties.md)   
 [Procedura: definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)