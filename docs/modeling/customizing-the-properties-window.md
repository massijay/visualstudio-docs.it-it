---
title: "Personalizzazione della finestra Propriet&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, Proprietà (finestra)"
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 20
---
# Personalizzazione della finestra Propriet&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile personalizzare l'aspetto e il comportamento della finestra delle proprietà nel linguaggio specifico di \(DSL\) dominio in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Nella definizione di modello DSL, definire le proprietà di dominio in ogni classe di dominio.  Per impostazione predefinita, quando si seleziona un'istanza della classe, in un diagramma o in Esplora Risorse di modello, ogni proprietà del dominio è elencato nella finestra delle proprietà.  Ciò consente di visualizzare e modificare i valori delle proprietà del dominio, anche se non ne è stato eseguito il mapping per formare i campi nel diagramma.  
  
## nomi, descrizioni e categorie  
 **nome e nome visualizzato**.  Nella definizione di una proprietà del dominio, il nome visualizzato della proprietà è il nome visualizzato di runtime nella finestra delle proprietà.  Al contrario, il nome viene utilizzato quando si scrive il codice programma per aggiornare la proprietà.  Il nome deve essere un nome alfanumerico corretto di CLR, ma il nome visualizzato può contenere spazi.  
  
 Quando si imposta il nome di una proprietà nella definizione di modello DSL, il relativo nome visualizzato sarà automaticamente impostato a una copia del nome.  Se si scrive un nome rivestito Pascal come “FuelGauge„, il nome visualizzato conterrà automaticamente uno spazio: “Contatore di combustibile„.  Tuttavia, è possibile impostare il nome visualizzato in modo esplicito a un altro valore.  
  
 **Descrizione**.  La descrizione di una proprietà del dominio viene visualizzato in due modi:  
  
-   Nella parte inferiore della finestra delle proprietà quando l'utente seleziona la proprietà.  È possibile utilizzarlo per spiegare che la proprietà rappresenta.  
  
-   Nel codice programma generato.  Se si utilizzano le funzionalità di documentazione per disegnare la documentazione di API, verrà visualizzato con la descrizione della proprietà nell'API.  
  
 **Categoria**.  Una categoria è un'intestazione nella Finestra Proprietà.  
  
## Esporre le funzionalità di stile  
 Alcune delle funzionalità dinamiche di elementi grafici possono essere rappresentate o *esposto* come proprietà di dominio.  Una funzionalità che è stata esposta in questo modo può essere aggiornata dall'utente e può più essere aggiornata dal codice programma.  
  
 Fare clic con il pulsante destro del mouse su una classe di forma nella definizione di modello DSL, quindi **aggiungere esposto**quindi scegliere una funzionalità.  
  
 Le forme è possibile esporre **FillColor**,  **OutlineColor**,  **TextColor**,  **OutlineDashStyle**,  **OutlineThickness** e  **FillGradientMode** proprietà.  I connettori è possibile esporre **colore**`,`**TextColor**,  **DashStyle**e  **spessore** proprietà.  I diagrammi è possibile esporre **FillColor** e  **TextColor** proprietà.  
  
## inoltrare: Visualizzazione delle proprietà degli elementi correlati  
 Quando l'utente del linguaggio DSL seleziona un elemento in un modello, le proprietà dell'elemento verranno visualizzate nella finestra delle proprietà.  Tuttavia, è anche possibile visualizzare le proprietà degli elementi correlati specificati.  Questa operazione è utile se è stato definito un gruppo di elementi che funziona con.  Ad esempio, è possibile definire un elemento principale e un elemento plug\-in facoltativo.  Se l'elemento principale è stato eseguito il mapping a una forma e l'altro no, è utile visualizzare tutte le relative proprietà come se fossero su un elemento.  
  
 questo effetto è denominato *l'inoltro della proprietà*e si verifica automaticamente in molti casi.  In altri casi, è possibile raggiungere la proprietà che inoltrate definire un descrittore di tipo del dominio.  
  
### Casi di inoltro di proprietà predefinito  
 Quando l'utente seleziona una forma o un connettore, o un elemento in Esplora Risorse, le proprietà verranno visualizzate nella Finestra Proprietà:  
  
-   Le proprietà del dominio definite nella classe di dominio dell'elemento del modello, inclusi quelli definiti nelle classi di base.  Un'eccezione è una proprietà del dominio per il quale è stato impostato **È visualizzabile** in  `False`.  
  
-   I nomi degli elementi collegati con relazioni con una molteplicità di 0..1.  Ciò fornisce un metodo pratico per visualizzare gli elementi collegati facoltativamente, anche se non definito un mapping del connettore per la relazione.  
  
-   Proprietà del dominio della relazione che utilizza destinato all'elemento.  Poiché incorporando le relazioni in genere non viene visualizzata in modo esplicito, questo consente di visualizzare le relative proprietà.  
  
-   Proprietà del dominio definite nella forma o sul connettore selezionata.  
  
### L'inoltro di aggiunta di proprietà  
 Per inoltrare una proprietà, definire un descrittore di tipo del dominio.  Se si dispone di una relazione di dominio tra due classi di dominio, è possibile utilizzare un descrittore di tipo del dominio per impostare una proprietà di dominio nella prima classe sul valore di una proprietà di dominio nella seconda classe di dominio.  Ad esempio, se si dispone di una relazione tra una classe di dominio del libro e una classe di dominio dell'autore, è possibile utilizzare un descrittore di tipo del dominio per impostare la proprietà del nome dell'autore di un libro visualizzati nella Finestra Proprietà quando l'utente seleziona il libro.  
  
> [!NOTE]
>  Proprietà che inoltra le ha effetto solo sulla Finestra Proprietà quando l'utente sta modificando un modello.  Non definisce una proprietà del dominio della classe ricevente.  Se si desidera accedere alla proprietà inoltrare il dominio in altre parti della definizione di modello DSL o nel codice programma, è necessario accedere all'elemento di inoltro.  
  
 La procedura riportata di seguito si presuppone che sia stato creato un modello DSL.  I passaggi i primi riepilogano i prerequisiti.  
  
##### Per inoltrare una proprietà da un altro elemento  
  
1.  Creare un oggetto [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione contenente almeno due classi, che in questo esempio vengono chiamate Book e autore.  Deve essere disponibile una relazione di qualsiasi tipo tra il libro e autore.  
  
     La molteplicità del ruolo di origine \(il ruolo sul lato del libro\) deve essere 0..1 o 1..1, in modo che ogni libro dispone di un autore.  
  
2.  in **DSL Esplora Risorse**, fare clic con il pulsante destro del mouse sulla classe di dominio del libro quindi fare clic su  **Aggiungere un nuovo DomainTypeDescriptor**.  
  
     un nodo denominato **Percorsi dei descrittori della proprietà personalizzata** viene visualizzata sotto  **descrittore di tipo personalizzato** nodo.  
  
3.  Fare clic con il pulsante destro del mouse **descrittore di tipo personalizzato** il nodo e quindi fare clic su  **Aggiungere un nuovo PropertyPath**.  
  
     Un nuovo percorso della proprietà viene visualizzata in **Percorsi dei descrittori della proprietà personalizzata** nodo.  
  
4.  Selezionare il nuovo percorso di proprietà e in **proprietà** finestra, impostare  **Percorso della proprietà** il percorso dell'elemento del modello adatto.  
  
     È possibile modificare il percorso in una visualizzazione struttura ad albero facendo clic sulla freccia giù a destra della proprietà.  Per ulteriori informazioni sui percorsi di dominio, vedere [Sintassi del percorso di dominio](../modeling/domain-path-syntax.md).  Quando è stata modificata, il percorso deve essere analogo a **BookReferencesAuthor.Author\/\! autore**.  
  
5.  set **proprietà** in  **Name** proprietà del dominio dell'autore.  
  
6.  set **nome visualizzato** per creare nome.  
  
7.  Trasformazione di tutti i modelli, compilare ed eseguire il modello DSL.  
  
8.  In un diagramma di modello, creare un libro, un autore e collegarle utilizzando la relazione di riferimento.  Selezionare l'elemento di pubblicazione e nella Finestra Proprietà viene visualizzato il nome dell'autore oltre alle proprietà del libro.  Modificare il nome dell'autore collegato, o collegare il libro a un autore diverso e osservare che il nome dell'autore del libro.  
  
## Editor di proprietà personalizzati  
 La finestra della proprietà fornisce un'esperienza predefinita appropriata di modifica per il tipo di ogni proprietà del dominio.  Ad esempio, per un tipo enumerato, riceverà un elenco a discesa e per una proprietà numerica, l'utente può immettere le cifre.  Ciò è applicabile solo ai tipi incorporati.  Se si specifica un tipo esterno, l'utente potrà visualizzare i valori della proprietà, ma non modificarlo.  
  
 Tuttavia, è possibile specificare gli editor e tipi:  
  
1.  Un altro editor utilizzato con un di tipo corrente.  Ad esempio, è possibile specificare un editor del percorso del file per una proprietà stringa.  
  
2.  Un tipo esterno della proprietà del dominio e un editor per.  
  
3.  Un editor di .NET quali l'editor del percorso del file, oppure è possibile creare diventi proprietaria editor di proprietà personalizzati.  
  
     Una conversione tra un tipo esterno e un tipo come stringa, con un editor predefinito.  
  
 In un linguaggio specifico di dominio, *tipo esterno* è qualsiasi tipo che non è uno dei tipi semplici \(quali boolean o Int32\) o della stringa.  
  
#### Per definire una proprietà di dominio che dispone di un tipo esterno  
  
1.  in **Esplora soluzioni**, aggiungere un riferimento a un assembly \(DLL\) che contiene il tipo esterno, in  **Dsl** progetto.  
  
     L'assembly può essere un assembly. tuttavia, o un assembly fornito dall'utente.  
  
2.  Aggiungere il tipo a **Tipi di dominio** elencare, a meno che non sia già stata ancora provveduto.  
  
    1.  Aprire DslDefinition.dsl e in **DSL Esplora Risorse**, fare clic con il pulsante destro del mouse sul nodo radice e scegliere  **aggiungere il nuovo tipo esterno**.  
  
         Una nuova voce verrà visualizzata in **Tipi di dominio** nodo.  
  
        > [!WARNING]
        >  La voce di menu è il nodo radice DSL, non **Tipi di dominio** nodo.  
  
    2.  Impostare il nome e lo spazio dei nomi del nuovo tipo nella Finestra Proprietà.  
  
3.  Aggiungere una proprietà di dominio a una classe di dominio nel modo usuale.  
  
     Nella Finestra Proprietà, selezionare il tipo esterno dall'elenco a discesa in **tipo** campo.  
  
 In questa fase, gli utenti possono visualizzare i valori della proprietà, ma non possono modificarlo.  I valori visualizzati sono ottenuti da `ToString()` funzione.  È possibile scrivere codice programma che imposta il valore della proprietà, ad esempio in un comando o in una regola.  
  
### impostare un editor di proprietà  
 Aggiungere un attributo CLR alla proprietà del dominio, nel formato seguente:  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 È possibile impostare l'attributo su una proprietà tramite **attributo personalizzato** voce nella Finestra Proprietà.  
  
 il tipo di `AnEditor` deve essere derivato dal tipo specificato nel secondo.  Il secondo parametro deve corrispondere a <xref:System.Drawing.Design.UITypeEditor> o  <xref:System.ComponentModel.ComponentEditor>.  Per ulteriori informazioni, vedere <xref:System.ComponentModel.EditorAttribute>.  
  
 È possibile specificare diventi proprietaria l'editor, o un editor fornito in [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], ad esempio  <xref:System.Windows.Forms.Design.FileNameEditor> o  <xref:System.Drawing.Design.ImageEditor>.  Ad esempio, attenersi alla procedura seguente per impostare una proprietà in cui l'utente può immettere un nome file.  
  
##### Per definire una proprietà di dominio nome file  
  
1.  Aggiungere una proprietà di dominio a una classe di dominio nella definizione di modello DSL.  
  
2.  selezionare la nuova proprietà.  in **attributo personalizzato** il campo della Finestra Proprietà, immettere il seguente attributo.  Per immettere questo attributo, fare clic sui puntini di sospensione **\[...\]** quindi digitare separatamente il nome di attributo e parametri:  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  Lasciare il tipo della proprietà del dominio sul valore predefinito di **stringa**.  
  
4.  Per verificare l'editor, verificare che gli utenti possano aprire l'editor di nome file per modificare la proprietà del dominio.  
  
    1.  Premere CTRL\+F5 o F5.  Nella soluzione di debug, aprire un file di test.  Creare un elemento della classe di dominio e selezionarlo.  
  
    2.  Nella Finestra Proprietà selezionare la proprietà, il dominio.  Il campo di valore vengono illustrati i puntini di sospensione **\[...\]**.  
  
    3.  Scegliere il pulsante con i puntini di sospensione.  Una finestra di dialogo File.  selezionare un file e chiudere la finestra di dialogo.  Il percorso del file è ora il valore della proprietà del dominio.  
  
### Definizione dell'editor di proprietà  
 È possibile definire diventi proprietaria l'editor.  A questo scopo per concedere all'utente o per modificare un tipo definito, o per modificare un di tipo corrente in modo speciale.  Ad esempio, è possibile consentire a chi introduca una stringa che rappresenta una formula.  
  
 Definire un editor scrittura di una classe derivata da <xref:System.Drawing.Design.UITypeEditor>.  la classe deve eseguire l'override:  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, per interagire con l'utente e aggiornare il valore della proprietà.  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, per specificare se verrà aperta una finestra di dialogo o verrà visualizzato un menu a discesa.  
  
 È anche possibile fornire una rappresentazione grafica del valore della proprietà visualizzate nella griglia delle proprietà.  A tale scopo, override `GetPaintValueSupported`e  `PaintValue`.  Per ulteriori informazioni, vedere <xref:System.Drawing.Design.UITypeEditor>.  
  
> [!NOTE]
>  Aggiungere il codice in un file di codice distinto in **Dsl** progetto.  
  
 Di seguito è riportato un esempio:  
  
```  
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor  
{  
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)  
  {  
    base.InitializeDialog(openFileDialog);  
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";  
    openFileDialog.Title = "Select a text file";  
  }  
}  
  
```  
  
 per utilizzare questo editor, impostare **attributo personalizzato** per una proprietà di un dominio a:  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Per ulteriori informazioni, vedere <xref:System.Drawing.Design.UITypeEditor>.  
  
## Creazione di un elenco a discesa di valori  
 È possibile fornire un elenco di valori che un utente scegliere da.  
  
> [!NOTE]
>  Questa tecnica viene fornito un elenco di valori che può cambiare in fase di esecuzione.  Se si desidera fornire un elenco che non cambia, considerare l'opportunità anziché utilizzando un tipo enumerato come tipo della proprietà del dominio.  
  
 Per definire un elenco di valori standard, si aggiunge l'oggetto alla proprietà del dominio un attributo CLR che presenta il formato seguente:  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 Definire una classe che deriva da <xref:System.ComponentModel.TypeConverter>.  aggiungere il codice in un file separato in **Dsl** progetto.  Di seguito è riportato un esempio:  
  
```c#  
/// <summary>  
/// Type converter that provides a list of values   
/// to be displayed in the property grid.  
/// </summary>  
/// <remarks>This type converter returns a list   
/// of the names of all "ExampleElements" in the   
/// current store.</remarks>  
public class MyTypeConverter : System.ComponentModel.TypeConverter  
{  
  /// <summary>  
  /// Return true to indicate that we return a list of values to choose from  
  /// </summary>  
  /// <param name="context"></param>  
  public override bool GetStandardValuesSupported  
    (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Returns true to indicate that the user has   
  /// to select a value from the list  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>If we returned false, the user would   
  /// be able to either select a value from   
  /// the list or type in a value that is not in the list.</returns>  
  public override bool GetStandardValuesExclusive  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Return a list of the values to display in the grid  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>A list of values the user can choose from</returns>  
  public override StandardValuesCollection GetStandardValues  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    // Try to get a store from the current context  
    // "context.Instance"  returns the element(s) that   
    // are currently selected i.e. whose values are being  
    // shown in the property grid.   
    // Note that the user could have selected multiple objects,   
    // in which case context.Instance will be an array.  
    Store store = GetStore(context.Instance);  
  
    List<string> values = new List<string>();  
  
    if (store != null)  
    {  
      values.AddRange(store.ElementDirectory  
        .FindElements<ExampleElement>()  
        .Select<ExampleElement, string>(e =>   
      {  
        return e.Name;  
      }));  
    }  
    return new StandardValuesCollection(values);  
  }  
  
  /// <summary>  
  /// Attempts to get to a store from the currently selected object(s)  
  /// in the property grid.  
  /// </summary>  
  private Store GetStore(object gridSelection)  
  {  
    // We assume that "instance" will either be a single model element, or   
    // an array of model elements (if multiple items are selected).  
  
    ModelElement currentElement = null;  
  
    object[] objects = gridSelection as object[];  
    if (objects != null && objects.Length > 0)  
    {  
      currentElement = objects[0] as ModelElement;  
    }  
    else  
    {  
        currentElement = gridSelection as ModelElement;  
    }  
  
    return (currentElement == null) ? null : currentElement.Store;  
  }  
  
}  
  
```  
  
## Vedere anche  
 [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)