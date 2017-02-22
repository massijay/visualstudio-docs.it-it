---
title: "L&#39;integrazione di modelli tramite Modelbus di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 26
caps.handback.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# L&#39;integrazione di modelli tramite Modelbus di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus fornisce un metodo per la creazione di collegamenti tra modelli e da altri strumenti ai modelli. Ad esempio, è possibile collegare i modelli di linguaggio specifico di dominio \(DSL\) e i modelli UML. È possibile creare un set integrato di DSL.  
  
 ModelBus consente di creare un riferimento univoco a un modello o a un elemento specifico all'interno di un modello. Questo riferimento può essere archiviato all'esterno del modello, ad esempio, in un elemento in un altro modello. Quando in un'occasione successiva, uno strumento vuole ottenere l'accesso all'elemento, l'infrastruttura ModelBus caricherà il modello appropriato e restituire l'elemento. Se si desidera, è possibile visualizzare il modello per l'utente. Se il file non è accessibile nella posizione precedente, ModelBus chiederà all'utente di trovarlo. Se si trova il file, ModelBus correggerà tutti i riferimenti a tale file.  
  
> [!NOTE]
>  Nell'attuale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implementazione di ModelBus, i modelli collegati deve corrispondere agli elementi nella stessa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione.  
  
 Per ulteriori informazioni e codice di esempio, vedere:  
  
-   [Procedura: aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md)  
  
-   [Modeling SDK per Visual Studio](http://www.microsoft.com/download/details.aspx?id=40754)  
  
##  <a name="provide"></a> Concede l'accesso a un linguaggio DSL  
 Prima di poter creare un riferimento ModelBus a un modello o ai relativi elementi, è necessario definire un ModelBusAdapter per il linguaggio DSL. Il modo più semplice per eseguire questa operazione è utilizzare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione ModelBus, che aggiunge comandi alla finestra di progettazione DSL.  
  
###  <a name="expose"></a> Per esporre una definizione DSL a ModelBus  
  
1.  Scaricare e installare l'estensione ModelBus di Visual Studio, a meno che non è già installato. Per ulteriori informazioni, vedere [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
2.  Aprire il file di definizione DSL. Fare doppio clic nell'area di progettazione e quindi fare clic su **Abilita Modelbus**.  
  
3.  Nella finestra di dialogo, scegliere **da esporre questo DSL a ModelBus**. È possibile scegliere entrambe le opzioni se si desidera che questo DSL esponga i propri modelli e usi riferimenti ad altri modelli.  
  
4.  Fare clic su **OK**. Un nuovo progetto "ModelBusAdapter" viene aggiunto alla soluzione DSL.  
  
5.  Se si desidera accedere il linguaggio DSL da un modello di testo, è necessario modificare il file AdapterManager.tt nel nuovo progetto. Omettere questo passaggio se si desidera accedere il linguaggio DSL da altro codice, ad esempio i comandi e gestori di eventi. Per altre informazioni, vedere [Utilizzo di ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
    1.  Modificare la classe base di adaptermanagerbase e impostarla su <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
    2.  Verso la fine del file, inserire questo attributo aggiuntivo davanti alla classe AdapterManager:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
    3.  Aggiungere i riferimenti del progetto ModelBusAdapter **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**.  
  
     Se si desidera accedere il linguaggio DSL dai modelli di testo e da altro codice, sono necessari due schede, uno modificato e uno non modificato.  
  
6.  Fare clic su **Trasforma tutti i modelli**.  
  
7.  Ricompilare la soluzione.  
  
 È ora possibile per ModelBus aprire le istanze di questo DSL.  
  
 La cartella `ModelBusAdapters\bin\*` contiene gli assembly compilati dal `Dsl` progetto e `ModelBusAdapters` progetto. Per fare riferimento a questo DSL da un altro linguaggio DSL, è necessario importare questi assembly.  
  
### Assicurarsi che gli elementi possono fare riferimento a  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Gli adattatori ModelBus utilizzano il guid di un elemento per identificarlo, per impostazione predefinita. Questi identificatori devono quindi essere persistenti nel file del modello.  
  
##### Per garantire tale elemento che ID vengono rese persistenti  
  
1.  Aprire il file Dsldefinition.  
  
2.  In Esplora DSL espandere **il comportamento di serializzazione Xml**, quindi **dati della classe**.  
  
3.  Per ogni classe a cui si desidera creare ModelBus fa riferimento a:  
  
     Fare clic sul nodo della classe e nella finestra Proprietà, accertarsi che **Id serializzare** è impostato su `true`.  
  
 In alternativa, se si desidera utilizzare nomi di elemento per identificare elementi anziché i GUID, è possibile sostituire parti degli adattatori generati. L'override dei metodi seguenti nella classe adapter:  
  
-   Eseguire l'override `GetElementId` per restituire l'ID a cui si desidera utilizzare. Questo metodo viene chiamato durante la creazione di riferimenti.  
  
-   Eseguire l'override `ResolveElementReference` per individuare l'elemento corretto da un riferimento ModelBus.  
  
##  <a name="editRef"></a> L'accesso a un linguaggio specifico di dominio da un altro linguaggio DSL  
 È possibile archiviare riferimenti ModelBus in una proprietà di dominio in un linguaggio DSL, ed è possibile scrivere codice personalizzato che li utilizza. È inoltre possibile consentire l'utente crea un riferimento ModelBus selezionando un file di modello e un elemento al suo interno.  
  
 Per abilitare l'utilizzo di riferimenti a un altro linguaggio specifico di dominio di un DSL, è innanzitutto necessario renderlo un *consumer* di riferimenti ModelBus.  
  
#### Per abilitare un DSL di usare riferimenti a un DSL esposto  
  
1.  Nel diagramma di definizione DSL, fare clic sulla parte principale del diagramma e quindi fare clic su **Abilita Modelbus**.  
  
2.  Nella finestra di dialogo, selezionare **si desidera abilitare questo modello per l'uso di riferimenti ModelBus**.  
  
3.  Nel progetto Dsl del DSL utilizzato, aggiungere gli assembly seguenti ai riferimenti del progetto. Questi assembly \(file con estensione dll\) sono disponibili nella directory ModelBusAdapter\\bin\\ \* del DSL esposto.  
  
    -   L'assembly DSL esposto, ad esempio **Fabrikam.FamilyTree.Dsl.dll**  
  
    -   Il modello esposto del bus di assembly dell'adattatore, ad esempio **Fabrikam.FamilyTree.ModelBusAdapter.dll**  
  
4.  Aggiungere gli assembly .NET seguenti ai riferimenti del progetto del progetto DSL consumer.  
  
    1.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
    2.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**  
  
#### Per archiviare un riferimento ModelBus in una proprietà di dominio  
  
1.  Nella definizione DSL del DSL utilizzato, aggiungere una proprietà di dominio a una classe di dominio e impostarne il nome.  
  
2.  Nelle proprietà di finestra con la proprietà di dominio selezionata, impostare **tipo** a `ModelBusReference`.  
  
 In questa fase, il codice del programma può impostare il valore della proprietà, ma è di sola lettura nella finestra Proprietà.  
  
 È possibile consentire agli utenti di impostare la proprietà con un editor di riferimento ModelBus specifico. Esistono due versioni dell'editor o *selezione:* uno che consente agli utenti di scegliere un file di modello e l'altra consente agli utenti di scegliere un file di modello e un elemento all'interno del modello.  
  
#### Per consentire all'utente di impostare un riferimento ModelBus in una proprietà di dominio  
  
1.  Fare doppio clic su proprietà di dominio e quindi fare clic su **proprietà specifiche di ModelBusReference modificare**. Verrà visualizzata una finestra di dialogo. Questo è il *selettore ModelBus*.  
  
2.  Selezionare un valore appropriato **tipo di ModelBusReference**: a un modello o a un elemento all'interno di un modello.  
  
3.  Nella stringa di filtro di finestra di dialogo file, immettere una stringa, ad esempio `Family Tree files |*.ftree`. Sostituire l'estensione del linguaggio DSL esposto.  
  
4.  Se si è scelto di fare riferimento a un elemento in un modello, è possibile aggiungere un elenco di tipi che l'utente può selezionare, ad esempio Company.FamilyTree.Person.  
  
5.  Fare clic su **OK**, quindi fare clic su **Trasforma tutti i modelli** nella barra degli strumenti di Esplora soluzioni.  
  
    > [!WARNING]
    >  Se non è stata selezionata un'entità o un modello valido, il pulsante OK non avrà effetto, sebbene possa sembrare abilitato.  
  
6.  Se è stato specificato un elenco di tipi di destinazione, come Company.FamilyTree.Person, quindi è necessario aggiungere un riferimento all'assembly al progetto DSL, che fa riferimento alla DLL del DSL di destinazione, ad esempio Company.FamilyTree.Dsl.dll  
  
#### Per testare un riferimento ModelBus  
  
1.  Compilare il DSL esposto e utilizzato.  
  
2.  Eseguire uno dei linguaggi specifici di dominio in modalità sperimentale premendo F5 o CTRL \+ F5.  
  
3.  Nel progetto di debug nell'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aggiungere i file che sono istanze di ogni DSL.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus può risolvere solo riferimenti a modelli di elementi nella stessa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione. Ad esempio, è possibile creare un riferimento a un file di modello in un'altra parte del file system.  
  
4.  Creare alcuni elementi e collegamenti nell'istanza del DSL esposto e salvarlo.  
  
5.  Aprire un'istanza del DSL utilizzato e selezionare un elemento del modello che dispone di una proprietà di riferimento ModelBus.  
  
6.  Nella finestra Proprietà, fare doppio clic su proprietà di riferimento ModelBus. Verrà visualizzata la finestra di dialogo di selezione.  
  
7.  Fare clic su **Sfoglia** e selezionare l'istanza del DSL esposto.  
  
     Il selettore inoltre consente di scegliere un elemento del modello, se è stato specificato il tipo specifico dell'elemento di riferimento ModelBus.  
  
## Creazione di riferimenti nel codice programma  
 Quando si desidera archiviare un riferimento a un modello o un elemento all'interno di un modello, si crea un `ModelBusReference`. Esistono due tipi di `ModelBusReference`: i riferimenti e i riferimenti agli elementi del modello.  
  
 Per creare un riferimento di modello, occorre l'AdapterManager del DSL di cui il modello è un'istanza e il nome del file o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] elemento di progetto del modello.  
  
 Per creare un riferimento all'elemento, è necessario un adattatore per il file di modello e l'elemento che si desidera fare riferimento a.  
  
> [!NOTE]
>  Con il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus, è possibile creare riferimenti solo agli elementi nella stessa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione.  
  
### Importare gli assembly DSL esposti  
 Nel progetto utilizzato, aggiungere i riferimenti agli assembly DSL e ModelBusAdapter del DSL esposto.  
  
 Ad esempio, si supponga che si desidera archiviare riferimenti ModelBus in elementi di un DSL MusicLibrary. I riferimenti ModelBus faranno riferimento agli elementi del DSL FamilyTree. Nel `Dsl` progetto della soluzione MusicLibrary, nel nodo dei riferimenti, aggiungere riferimenti agli assembly seguenti:  
  
-   Fabrikam.FamilyTree.Dsl.dll \- DSL esposto.  
  
-   Fabrikam.FamilyTree.ModelBusAdapters.dll \- adattatore ModelBus del DSL esposto.  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0  
  
 Questi assembly sono reperibili il `ModelBusAdapters` progetto del DSL esposto, in `bin\*`.  
  
 Nel file di codice in cui si creeranno i riferimenti, in genere è necessario importare questi spazi dei nomi:  
  
```  
// The namespace of the DSL you want to reference:  
using Fabrikam.FamilyTree;  // Exposed DSL  
using Fabrikam.FamilyTree.ModelBusAdapters;  
using Microsoft.VisualStudio.Modeling.Integration;  
using System.Linq;  
...  
```  
  
### Per creare un riferimento a un modello  
 Per creare un riferimento di modello, accedere all'AdapterManager per il DSL esposto e usarlo per creare un riferimento al modello. È possibile specificare un percorso di file, o un `EnvDTE.ProjectItem`.  
  
 Da AdapterManager è possibile ottenere un adattatore, che fornisce l'accesso ai singoli elementi nel modello.  
  
> [!NOTE]
>  Quando viene completato, è necessario eliminare un Adapter. È il modo più semplice per ottenere questo risultato con un `using` istruzione. Questa condizione è illustrata nell'esempio seguente.  
  
```  
// The file path of a model instance of the FamilyTree DSL:  
string targetModelFile = "TudorFamilyTree.ftree";  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Get an adapterManager for the target DSL:  
FamilyTreeAdapterManager manager =   
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)   
     as FamilyTreeAdapterManager;  
// or: (modelBus.FindAdapterManagers(targetModelFile).First())  
// or could provide an EnvDTE.ProjectItem  
  
// Create a reference to the target model:  
// NOTE: the target model must be a file in this project.  
ModelBusReference modelReference =  
     manager.CreateReference(targetModelFile);  
// or can use an EnvDTE.ProjectItem instead of the filename  
  
// Get the root element of this model:  
using (FamilyTreeAdapter adapter =   
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)  
{  
  FamilyTree modelRoot = adapter.ModelRoot;  
  // Access elements under the root in the usual way:  
  foreach (Person p in modelRoot.Persons) {...}  
  // You can create adapters for individual elements:  
  ModelBusReference elementReference =  
     adapter.GetElementReference(person);  
  ...  
} // Dispose adapter  
  
```  
  
 Se si desidera essere in grado di utilizzare `modelReference` in un secondo momento, è possibile archiviarlo in una proprietà di dominio che dispone del tipo esterno `ModelBusReference`:  
  
```  
using Transaction t = this.Store.TransactionManager  
    .BeginTransaction("keep reference"))  
{  
  artist.FamilyTreeReference = modelReference;  
  t.Commit();  
}  
```  
  
 Per consentire agli utenti di modificare questa proprietà di dominio, utilizzare `ModelReferenceEditor` come parametro nell'attributo Editor. Per ulteriori informazioni, vedere [consente all'utente di modificare un riferimento](#editRef).  
  
### Per creare un riferimento a un elemento  
 L'adapter creato per il modello consente di creare e risolvere i riferimenti.  
  
```  
// person is an element in the FamilyTree model:  
ModelBusReference personReference =   
  adapter.GetElementReference(person);  
```  
  
 Se si desidera essere in grado di utilizzare `elementReference` in un secondo momento, è possibile archiviarlo in una proprietà di dominio che dispone del tipo esterno `ModelBusReference`. Per consentire agli utenti di modificarla, usare `ModelElementReferenceEditor` come parametro nell'attributo Editor. Per ulteriori informazioni, vedere [consente all'utente di modificare un riferimento](#editRef).  
  
### Risoluzione dei riferimenti  
 Se si dispone di un `ModelBusReference` \(MBR\) è possibile ottenere il modello o l'elemento del modello a cui fa riferimento. Se l'elemento è presentato in un diagramma o altra visualizzazione, è possibile aprire la visualizzazione e selezionare l'elemento.  
  
 È possibile creare un adattatore da un MBR. Dalla scheda, è possibile ottenere la radice del modello. È anche possibile risolvere gli MBR che fanno riferimento a elementi specifici all'interno del modello.  
  
```  
using Microsoft.VisualStudio.Modeling.Integration; ...  
ModelBusReference elementReference = ...;  
  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Use a model reference or an element reference  
// to obtain an adapter for the target model:  
using (FamilyTreeAdapter adapter =   
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)  
   // or CreateAdapter(modelReference)  
{  
  // Get the root of the model:  
  FamilyTree tree = adapter.ModelRoot;  
  
  // Get a model element:  
  MyDomainClass mel =  
    adapter.ResolveElementReference<MyDomainClass>(elementReference);  
  if (mel != null) {...}  
  
  // Get the diagram or other view, if there is one:  
  ModelBusView view = adapter.GetDefaultView();  
  if (view != null)   
  {  
   view.Open();  
   // Display the diagram:  
   view.Show();   
   // Attempt to select the shape that presents the element:  
   view.SetSelection(elementReference);  
  }  
} // Dispose the adapter.  
```  
  
##### Per risolvere riferimenti ModelBus in un modello di testo  
  
1.  Il linguaggio DSL si desidera accedere è necessario un adattatore ModelBus configurato per l'accesso dai modelli di testo. Per altre informazioni, vedere [Concede l'accesso a un linguaggio DSL](#provide).  
  
2.  In genere, si accederà a una destinazione DSL utilizzando un modello di Bus di riferimento \(MBR\) archiviato in un linguaggio DSL di origine. Il modello include pertanto la direttiva del linguaggio DSL di origine e codice per risolvere il MBR. Per ulteriori informazioni sui modelli di testo, vedere [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
    ```  
    <#@ template debug="true" hostspecific="true"   
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "System.Core" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="Company.CompartmentDragDrop" #>  
    <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>  
    <# // Get source root from directive processor:  
      ExampleModel source = this.ExampleModel;   
      // This DSL has a MBR in its root:  
    using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)   
      {  
      ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();  
      ModelBusReference modelReference =  
        manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));  
  
      // Get the root element of this model:  
      using (CompartmentDragDropAdapter adapter =   
         this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)  
      {  
        ModelRoot root = adapter.ModelRoot;  
    #>  
    [[<#= root.Name #>]]  
    <#  
      }  
    #>  
  
    ```  
  
 Per ulteriori informazioni e una procedura dettagliata, vedere [Utilizzo di ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md)  
  
## La serializzazione di un ModelBusReference  
 Se si desidera archiviare un `ModelBusReference` \(MBR\) sotto forma di stringa, è possibile serializzarlo:  
  
```  
string serialized = modelBus.SerializeReference(elementReference);  
// Store it anywhere, then get it back again:  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, null);  
```  
  
 Un MBR serializzato in questo modo è indipendente dal contesto. Se si utilizza il semplice basato su file adattatore ModelBus, il MBR contiene un percorso file assoluto. Ciò è sufficiente se i file di modello di istanza non verranno spostata. Tuttavia, i file del modello sarà in genere gli elementi in un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto. Gli utenti verranno si aspettano di essere in grado di spostare l'intero progetto a diverse parti del file system. Sono inoltre prevedere la possibilità di mantenere il progetto nel controllo del codice sorgente e aprirlo in computer diversi. I nomi di percorso devono essere serializzati pertanto relativa al percorso del progetto che contiene i file.  
  
### La serializzazione relativo a un percorso di File specificato  
 Oggetto `ModelBusReference` contiene un `ReferenceContext`, ovvero un dizionario in cui è possibile archiviare informazioni quali il percorso del file rispetto al quale deve essere serializzato.  
  
 Per serializzare relativo a un percorso:  
  
```  
elementReference.ReferenceContext.Add(  
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,   
   currentProjectFilePath);  
string serialized = modelBus.SerializeReference(elementReference);  
```  
  
 Per recuperare il riferimento dalla stringa:  
  
```  
ReferenceContext context = new ReferenceContext();  
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,  
    currentProjectFilePath);  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, context);  
```  
  
### Riferimenti ModelBus creati da altri adattatori  
 Le informazioni seguenti sono utili se si desidera creare un adattatore personalizzato.  
  
 Oggetto `ModelBusReference` \(MBR\) è costituito da due parti: l'intestazione MBR, che viene deserializzata da ModelBus, e un adapter specifico che viene gestita dal gestore dell'adattatore specifico. Ciò consente di fornire il proprio formato di serializzazione dell'adattatore. Ad esempio, si può fare riferimento a un database anziché in un file oppure è possibile memorizzare informazioni aggiuntive nel riferimento dell'adattatore. Un adattatore personalizzato può inserire informazioni aggiuntive nel `ReferenceContext`.  
  
 Quando si deserializza un MBR, è necessario fornire un ReferenceContext che viene quindi archiviato nell'oggetto MBR. Quando si serializza un MBR, il ReferenceContext archiviato viene utilizzato dall'adattatore per generare la stringa. La stringa deserializzata non contiene tutte le informazioni contenute in ReferenceContext. Ad esempio, nell'adattatore semplice basato su file, ReferenceContext contiene un percorso del file radice che non è archiviato nella stringa MBR serializzata.  
  
 il MBR viene deserializzato in due fasi:  
  
-   `ModelBusReferencePropertySerializer` è il serializzatore standard che gestisce l'intestazione MBR. Viene utilizzato il linguaggio DSL standard `SerializationContext` contenitore delle proprietà, che viene archiviato nel `ReferenceContext` utilizzando la chiave `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`. In particolare, il `SerializationContext` deve contenere un'istanza di `ModelBus`.  
  
-   L'adattatore ModelBus gestisce la parte specifica dell'adapter del MBR. È possibile utilizzare informazioni aggiuntive archiviate nel Contextreference del MBR. L'adattatore semplice basato su file mantiene i percorsi di file radice usando i tasti `FilePathLoadContextKey` e `FilePathSaveContextKey`.  
  
     Riferimento dell'adattatore in un file di modello è deserializzato solo quando viene utilizzato.  
  
## Per creare un modello  
  
### Creazione, apertura e la modifica di un modello  
 Nel frammento seguente è tratto dall'esempio di macchina a stati nel sito Web VMSDK. Viene illustrato l'uso di ModelBusReferences per creare e aprire un modello e per ottenere il diagramma associato al modello.  
  
 In questo esempio, il nome del DSL di destinazione è StateMachine. Diversi nomi sono derivati da esso, ad esempio il nome della classe del modello e il nome dell'adattatore ModelBus.  
  
```  
using Fabrikam.StateMachine.ModelBusAdapters;   
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Integration;  
using Microsoft.VisualStudio.Modeling.Integration.Shell;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
// Create a new model.  
ModelBusReference modelReference =   
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);  
//Keep reference of new model in this model.  
using (Transaction t = ...)  
{  
  myModelElement.ReferenceProperty = modelReference;  
  t.Commit();  
}  
// Get the ModelBus service from Visual Studio.  
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.  
    GetGlobalService(typeof(SModelBus)) as IModelBus;  
// Get a modelbus adapter on the new model.  
ModelBusAdapter modelBusAdapter;  
modelBus.TryCreateAdapter(modelReference,   
    this.ServiceProvider, out modelBusAdapter);  
using (StateMachineAdapter adapter =   
      modelBusAdapter as StateMachineAdapter)  
{  
    if (adapter != null)  
    {  
        // Obtain a Diagram from the adapter.  
        Diagram targetDiagram =   
           ((StandardVsModelingDiagramView)  
                 adapter.GetDefaultView()  
            ).Diagram;  
  
        using (Transaction t =   
             targetDiagram.Store.TransactionManager  
                .BeginTransaction("Update diagram"))  
        {  
            DoUpdates(targetDiagram);  
            t.Commit();  
        }  
  
        // Display the new diagram.  
        adapter.GetDefaultView().Show();  
    }  
}  
```  
  
## Convalidare i riferimenti  
 Brokenreferencedetector esegue il test di tutte le proprietà di dominio in un archivio che può contenere riferimenti ModelBus. Chiama l'azione che forniscono in cui viene trovata alcuna azione. Ciò è particolarmente utile per i metodi di convalida. Il seguente metodo di convalida verifica l'archivio nel tentativo di salvare il modello e segnala i riferimenti interrotti nella finestra degli errori:  
  
```  
[ValidationMethod(ValidationCategories.Save)]  
public void ValidateModelBusReferences(ValidationContext context)  
{  
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,  
    delegate(ModelElement element, // parent of property  
             DomainPropertyInfo property, // identifies property  
             ModelBusReference reference) // invalid reference  
    {   
      context.LogError(string.Format(INVALID_REF_FORMAT,   
             property.Name,   
             referenceState.Name,   
             new ModelBusReferenceTypeConverter().  
                 ConvertToInvariantString(reference)),   
         "Reference",   
         element);  
      });  
}}  
private const string INVALID_REF_FORMAT =   
    "The '{0}' domain property of ths ReferenceState instance "  
  + "named '{1}' contains reference value '{2}' which is invalid";  
```  
  
## Azioni eseguite dall'estensione ModelBus  
 Le informazioni seguenti non sono essenziale, ma potrebbero essere utili se si fa uso intensivo di ModelBus.  
  
 L'estensione ModelBus apporta le modifiche seguenti alla soluzione DSL.  
  
 Facendo clic su diagramma di definizione DSL, fare clic su **Abilita Modelbus**, quindi selezionare **Abilita questo DSL per l'uso di ModelBus**:  
  
-   Nel progetto DSL viene aggiunto un riferimento a **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
-   Nella definizione DSL, viene aggiunto un riferimento di tipo esterno: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.  
  
     È possibile visualizzare il riferimento in **Esplora DSL**, in **tipi di dominio**. Per aggiungere manualmente riferimenti di tipo esterno, fare clic sul nodo radice.  
  
-   Viene aggiunto un nuovo file modello, **Dsl\\GeneratedCode\\ModelBusReferencesSerialization.tt**.  
  
 Quando si imposta il tipo della proprietà del dominio su ModelBusReference e quindi fare doppio clic su proprietà e fare clic su **proprietà specifiche di ModelBusReference abilitare**:  
  
-   Diversi attributi CLR vengono aggiunti alla proprietà del dominio. È possibile visualizzarli nel campo attributi personalizzati nella finestra Proprietà. In **Dsl\\GeneratedCode\\DomainClasses.cs**, è possibile visualizzare gli attributi nella dichiarazione della proprietà:  
  
    ```  
    [System.ComponentModel.TypeConverter(typeof(  
    Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]  
    [System.ComponentModel.Editor(typeof(  
      Microsoft.VisualStudio.Modeling.Integration.Picker  
      .ModelReferenceEditor // or ModelElementReferenceEditor  
      ), typeof(System.Drawing.Design.UITypeEditor))]  
    [Microsoft.VisualStudio.Modeling.Integration.Picker  
      .SupplyFileBasedBrowserConfiguration  
      ("Choose a model file", "Target model|*.target")]  
    ```  
  
 Quando si fare clic nel diagramma di definizione DSL, fare clic su **Abilita ModelBus**, e selezionare **Esponi questo DSL a ModelBus**:  
  
-   Un nuovo progetto `ModelBusAdapter` viene aggiunto alla soluzione.  
  
-   Un riferimento a `ModelBusAdapter` viene aggiunto per il `DslPackage` progetto.`ModelBusAdapter` contiene un riferimento di `Dsl` progetto.  
  
-   In **DslPackage\\source.extention.tt**, `|ModelBusAdapter|` viene aggiunto come componente MEF.  
  
## Vedere anche  
 [Procedura: aprire un modello da file nel codice del programma](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Integrate UML models with other models and tools](../modeling/integrate-uml-models-with-other-models-and-tools.md)   
 [Procedura: aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Utilizzo di ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md)