---
title: "Utilizzo di ModelBus di Visual Studio in un modello di testo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 13
caps.handback.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Utilizzo di ModelBus di Visual Studio in un modello di testo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se si scrivono modelli di testo che indicano un modello contenente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Riferimento ModelBus, potrebbe essere necessario risolvere i riferimenti per accedere ai modelli destinazione.  In tal caso, è necessario adattare i modelli di testo e linguaggi specifici di dominio a cui si fa \(DSLs\) riferimento:  
  
-   Il modello DSL di destinazione dei riferimenti necessario disporre di un adattatore ModelBus configurato per l'accesso dai modelli di testo.  Se inoltre si accede al modello DSL da altro codice, l'adattatore riconfigurato come è obbligatorio oltre all'adattatore standard ModelBus.  
  
     L'amministratore di deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> e deve disporre dell'attributo  `[HostSpecific(HostName)]`.  
  
-   il modello deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
> [!NOTE]
>  Se si desidera leggere modelli DSL che non contengono riferimenti ModelBus, è possibile utilizzare i processori di direttiva che vengono generati nei progetti di modello DSL.  Per ulteriori informazioni, vedere [Accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md).  
  
 Per ulteriori informazioni sui modelli di testo, vedere [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
## Creare un adattatore di template bus\) per accedere dai modelli di testo  
 Per risolvere un riferimento ModelBus nel modello di testo, la destinazione DSL necessario disporre di un adattatore compatibile.  Modelli di testo di esecuzione in un AppDomain separato da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] documentare gli editor e quindi l'adattatore necessario caricare il modello anziché accedere all'oggetto DTE.  
  
#### Per creare un adattatore ModelBus compatibile con i modelli di testo  
  
1.  Se la soluzione DSL di destinazione non dispone di un oggetto **ModelBusAdapter** il progetto, ne viene creato uno tramite la procedura guidata di estensione Modelbus:  
  
    1.  scaricare e installare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Estensione ModelBus, se non è stato già fatto.  Per ulteriori informazioni, vedere [L'sdk di visualizzazione e modellazione](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Aprire il file di definizione DSL.  Fare clic con il pulsante destro del mouse sull'area di progettazione e scegliere **abilitare Modelbus**.  
  
    3.  Nella finestra di dialogo, selezionare **Si desidera esporre il modello DSL a ModelBus**.  È possibile selezionare entrambe le opzioni per ottenere questo modello DSL sia per esporre i relativi modelli che per utilizzare i riferimenti all'altro DSLs.  
  
    4.  Scegliere **OK**.  Un nuovo progetto “ModelBusAdapter„ aggiunto alla soluzione DSL.  
  
    5.  Fare clic su **Trasformazione di tutti i modelli**.  
  
    6.  Ricompilare la soluzione.  
  
2.  Se si desidera accedere al modello DSL sia da un modello di testo che da altro codice, come comando, duplicato **ModelBusAdapter** progetto:  
  
    1.  In Esplora risorse, copiare e incollare la cartella contenente **ModelBusAdapter.csproj**.  
  
    2.  Rinominare il file di progetto, ad esempio **T4ModelBusAdapter.csproj**\).  
  
    3.  in **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nodo della soluzione, quindi  **aggiungere**quindi scegliere  **progetto esistente**.  Individuare il nuovo progetto dell'adattatore, **T4ModelBusAdapter.csproj**.  
  
    4.  In ognuno `*.tt` il file del nuovo progetto, modificare lo spazio dei nomi.  
  
    5.  Fare clic con il pulsante destro del mouse sul nuovo progetto in Esplora soluzioni e scegliere proprietà.  Nell'editor delle proprietà, modificare i nomi dell'assembly generato e dello spazio dei nomi predefinito.  
  
    6.  Nel progetto DslPackage, aggiungere un riferimento al nuovo progetto dell'adattatore in modo che contenga riferimenti a entrambi gli adattatori.  
  
    7.  In DslPackage \\ source.extension.tt, aggiungere una riga che fa riferimento al nuovo progetto dell'adattatore.  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **Trasformazione di tutti i modelli** e ricompilare la soluzione.  Nessun errore di compilazione deve verificarsi.  
  
3.  Nel nuovo progetto dell'adattatore, aggiungere riferimenti agli assembly seguenti:  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  In AdapterManager.tt:  
  
    -   modificare la dichiarazione di AdapterManagerBase in modo che erediti da <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   Alla fine del file, sostituire l'attributo di HostSpecific prima che la classe di AdapterManager.  Rimuovere la riga seguente:  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         Inserire la seguente riga:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Questo attributo consente di filtrare il set di adattatori che è disponibile quando un utente modelbus cerca un adattatore.  
  
5.  **Trasformazione di tutti i modelli** e ricompilare la soluzione.  Nessun errore di compilazione deve verificarsi.  
  
## Scrive un modello di testo che può risolvere i riferimenti a ModelBus  
 In genere, si inizia con un modello che indica e file “da un database di origine„ DSL.  Questo modello utilizza la direttiva generata nel progetto di modello DSL di origine leggere i file di modello originali nel modo descritto in [Accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md).  Tuttavia, l'origine DSL contiene riferimenti ModelBus “a una destinazione„ DSL.  Pertanto si desidera consentire al codice del modello per risolvere i riferimenti e accedere al database di destinazione DSL.  È necessario adattare il modello seguendo questi passaggi:  
  
-   Modificare la classe di base del modello a <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
-   Importare `hostspecific="true"` nella direttiva del modello.  
  
-   Aggiungere i riferimenti ad assembly al database di destinazione DSL e il relativo adattatore e abilitare ModelBus.  
  
-   Non è necessaria la direttiva che venga generata come parte del database di destinazione DSL.  
  
```  
<#@ template debug="true" hostspecific="true" language="C#"  
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
<#@ output extension=".txt" #>  
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>  
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>  
<#@ assembly name = "System.Core" #>  
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
<#@ import namespace="Company.TargetDsl" #>  
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>  
<#@ import namespace="System.Linq" #>  
<#  
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.  
  // In the source DSL Definition, the root element has a model reference:  
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)   
  {if (adapter != null)  
   {  
      // Get the root of the target model:  
      TargetRoot target = adapter.ModelRoot;  
    // The source DSL Definition has a class "SourceElement" embedded under the root.  
    // (Let’s assume they’re all in the same model file):  
    foreach (SourceElement sourceElement in source.Elements)  
    {  
      // In the source DSL Definition, each SourceElement has a MBR property:  
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;  
      // Resolve the target model element:   
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);   
#>  
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.  
<#  
    }  
  }}  
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename   
  // from a path that is relative to the text template.  
#>  
  
```  
  
 Quando questo modello di testo viene eseguito, `SourceDsl` la direttiva carica il file  `Sample.source`.  Il modello può accedere agli elementi del modello, a partire da `this.ModelRoot`.  Il codice può utilizzare le classi di dominio e le proprietà del modello DSL.  
  
 Inoltre, il modello può risolvere i riferimenti a ModelBus.  La posizione del punto di riferimenti al modello di destinazione, le direttive dell'assembly let l'utilizzo di codice le classi di dominio e le proprietà DSL del modello.  
  
-   Se non si utilizza una direttiva che venga generata da un progetto di modello DSL, è inoltre necessario includere quanto segue.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   utilizzo `this.ModelBus` per ottenere accesso a ModelBus.  
  
## procedura dettagliata: Testato un modello di testo che utilizza ModelBus  
 In questa procedura dettagliata, è necessario seguire questi passaggi:  
  
1.  costrutto due DSLs.  Un linguaggio specifico di dominio, utente, corrisponde a `ModelBusReference` proprietà che può fare riferimento a un altro modello DSL, provider.  
  
2.  Creare due adattatori ModelBus nel provider: uno per l'accesso dai modelli di testo, l'altro per il codice comune di.  
  
3.  Creare modelli dell'istanza del DSLs in un singolo progetto sperimentale.  
  
4.  Impostare una proprietà di dominio in un modello per indicare un altro modello.  
  
5.  Scrivere un gestore di fare doppio clic su per visualizzare il modello a cui si fa riferimento.  
  
6.  Scrivere un modello di testo che può caricare il primo modello, seguire il riferimento all'altro modello e quindi l'altro modello.  
  
#### Creare un modello DSL accessibile a ModelBus  
  
1.  Creare una nuova soluzione DSL.  Per questo esempio, selezionare il modello della soluzione flusso di attività.  Impostare il nome della lingua a `MBProvider` e l'estensione di file “a .provide„.  
  
2.  Nel diagramma della definizione di modello DSL, fare clic con il pulsante destro del mouse su una parte vuota del diagramma che non si trova nella parte superiore e quindi fare clic su **abilitare Modelbus**.  
  
    -   Se non viene visualizzato **abilitare Modelbus**, è necessario scaricare e installare l'estensione VMSDK ModelBus.  Ricerca del sito VMSDK: [L'sdk di visualizzazione e modellazione](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  in **abilitare Modelbus** finestra di dialogo, selezionare  **Esporre il modello DSL a ModelBus**quindi scegliere  **Scegliere OK**.  
  
     un nuovo progetto, `ModelBusAdapter`, viene aggiunto alla soluzione.  
  
 A questo punto si dispone di un modello DSL accessibile dai modelli di testo con ModelBus.  I riferimenti a possono essere risolti nel codice dei controlli, i gestori eventi, o delle regole, che vengono eseguiti nell'appdomain dell'editor del file modello.  Tuttavia, l'esecuzione dei modelli di testo in un AppDomain separato e non può accedere un modello quando viene modificata.  Se si desidera accedere ai riferimenti ModelBus a questo modello DSL da un modello di testo, è necessario disporre di un ModelBusAdapter separato.  
  
#### Per creare un adattatore ModelBus configurato per i modelli di testo  
  
1.  In Esplora risorse, copiare e incollare la cartella che contiene ModelBusAdapter.csproj.  
  
     denominare la cartella T4ModelBusAdapter.  
  
     rinominare il file di progetto T4ModelBusAdapter.csproj.  
  
2.  In Esplora soluzioni, aggiungere T4ModelBusAdapter alla soluzione di MBProvider.  Fare clic con il pulsante destro del mouse sul nodo della soluzione, quindi **aggiungere**quindi scegliere  **progetto esistente**.  
  
3.  Fare clic con il pulsante destro del mouse sul nodo del progetto di T4ModelBusAdapter e scegliere proprietà.  Nella finestra delle proprietà del progetto, modificare **Nome assembly** e  **Spazio dei nomi predefinito** in  `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  In ogni file di \*.tt in T4ModelBusAdapter, inserisci “T4„ nell'ultima parte dello spazio dei nomi, in modo che la riga simile al seguente.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  in `DslPackage` il progetto, aggiungere un riferimento di progetto a  `T4ModelBusAdapter`.  
  
6.  In DslPackage \\ source.extension.tt, aggiungere la riga seguente in `<Content>`.  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  in `T4ModelBusAdapter` il progetto, aggiungere un riferimento a:  **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  aprire T4ModelBusAdapter \\AdapterManager .tt:  
  
    1.  modificare la classe di base di AdapterManagerBase a <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  In questa parte del file è ora simile al seguente.  
  
        ```  
        namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters  
        {  
            /// <summary>  
            /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer  
            /// </summary>  
            public partial class <#= dslName #>AdapterManagerBase   
            : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager  
            {  
  
        ```  
  
    2.  Alla fine del file, inserire il seguente attributo aggiuntivo davanti alla classe AdapterManager.  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Il risultato sarà simile al seguente.  
  
        ```  
        /// <summary>  
        /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter  
        /// </summary>  
        [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]  
        [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]  
        [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]  
        [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]  
        public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase  
        {  
        }  
  
        ```  
  
9. Fare clic su **Trasformazione di tutti i modelli** nella barra del titolo di Esplora soluzioni.  
  
10. Ricompilare la soluzione.  Fare clic su F5.  
  
11. Verificare che il modello DSL funziona premendo F5.  Nel progetto sperimentale, aprire `Sample.provider`.  Chiudere l'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 I riferimenti ModelBus a questo modello DSL possono ora essere risolti nei modelli di testo e anche nel codice comune.  
  
#### Creare un modello DSL a una proprietà del dominio di riferimento ModelBus  
  
1.  Creare un nuovo modello DSL utilizzando il modello minimo della soluzione del linguaggio.  denominare il linguaggio MBConsumer e impostare l'estensione di file “a .consume„.  
  
2.  Nel progetto di modello DSL, aggiungere un riferimento all'assembly di MBProvider DSL.  Fare clic con il pulsante destro del mouse  `MBConsumer\Dsl\References` quindi scegliere  **aggiungere il riferimento**.  in **Navigazione** la scheda, individua  `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     Questo consente di creare codice che utilizza un altro modello DSL.  Se si desidera creare riferimenti ai diversi DSLs, aggiungerli anche.  
  
3.  Nel diagramma della definizione di modello DSL, fare clic con il pulsante destro del mouse sul diagramma e scegliere **abilitare ModelBus**.  Nella finestra di dialogo, selezionare **Consentire a questo modello DSL per utilizzare il ModelBus**.  
  
4.  Nella classe `ExampleElement`, aggiungere una nuova proprietà del dominio  `MBR`e nella Finestra Proprietà, impostare il tipo su  `ModelBusReference`.  
  
5.  Fare clic con il pulsante destro del mouse sulla proprietà del dominio nel diagramma e scegliere **modificare le proprietà specifiche di ModelBusReference**.  Nella finestra di dialogo, selezionare **un elemento del modello**.  
  
     Impostare il filtro dalla finestra di dialogo file al seguente.  
  
     `Provider File|*.provide`  
  
     la sottostringa dopo “&#124;„ è un filtro per la finestra di dialogo di selezione file.  È possibile impostarlo per consentire tutti i file tramite \*.\*  
  
     in **Tipo di elemento del modello** l'elenco, i nomi di un öre più classi di dominio nel provider DSL \(ad esempio, Company.MBProvider.Task\).  È possibile classi astratte.  Se si lascia vuota dell'elenco, l'utente può impostare il riferimento a qualsiasi elemento.  
  
6.  chiudere la finestra di dialogo e **Trasformazione di tutti i modelli**.  
  
 È stato creato un modello DSL che può contenere riferimenti agli elementi in un altro linguaggio DSL.  
  
#### Creare un riferimento ModelBus a un altro file nella soluzione  
  
1.  Nella soluzione di MBConsumer, premere CTRL\+F5.  un'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verrà aperto in  **MBConsumer\\Debugging** progetto.  
  
2.  Aggiungere una copia di Sample.provide a **MBConsumer\\Debugging** progetto.  Questa operazione è necessaria perché un riferimento ModelBus deve fare riferimento a un file nella stessa soluzione.  
  
    1.  Fare clic con il pulsante destro del mouse sul progetto di debug, quindi **aggiungere**quindi scegliere  **elemento esistente**.  
  
    2.  in **aggiungere l'elemento** la finestra di dialogo, impostare il filtro su  **Tutti i file \(\*.\*\)**.  
  
    3.  Passa a `MBProvider\Debugging\Sample.provide` quindi scegliere  **aggiungere**.  
  
3.  Aprire `Sample.consume`.  
  
4.  Fare clic su una forma di esempio e nella Finestra Proprietà, fare clic su **\[...\]** nella proprietà di MBR.  Nella finestra di dialogo, fare clic su **Navigazione** e selezionare  `Sample.provide`.  Nella finestra di elementi, espandere l'attività del tipo e selezionare uno degli elementi.  
  
5.  Salvare il file.  
  
     \(Non ancora chiudere l'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\).  
  
 È stato creato un modello contenente un riferimento ModelBus a un elemento in un altro modello.  
  
#### Risolvere un riferimento ModelBus nel modello di testo  
  
1.  Nell'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aprire un file modello di testo di esempio.  Impostare il proprio contenuto come segue.  
  
    ```  
    <#@ template debug="true" hostspecific="true" language="C#"  
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="Company.MBProvider" #>  
    <#  
      // Property provided by the Consumer directive processor:  
      ExampleModel consumerModel = this.ExampleModel;   
      // Iterate through Consumer model, listing the elements:  
      foreach (ExampleElement element in consumerModel.Elements)  
      {  
    #>  
       <#= element.Name #>   
    <#  
        if (element.MBR != null)  
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))  
      {   
              // If we allowed multiple types or DSLs in the MBR, discover type here.  
        Task task = adapter.ResolveElementReference<Task>(element.MBR);  
    #>  
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>  
    <#  
          }  
      }  
    #>  
  
    ```  
  
     Osservare i punti seguenti:  
  
    1.  `hostSpecific` e  `inherits` attributi di  `template` la direttiva deve essere impostata su.  
  
    2.  Il modello consumer viene eseguito nel modo consueto dal processore di direttiva generato in tale modello DSL.  
  
    3.  Direttive di importazione e dell'assembly siano in grado di accedere a ModelBus e tipi di provider DSL.  
  
    4.  Se si è certi che molti MBR sono collegati allo stesso modello, è preferibile chiamare CreateAdapter solo una volta.  
  
2.  Salvare il modello.  Verificare che il file di testo risultante sia simile al seguente.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### Risolvere un riferimento ModelBus in un gestore movimenti  
  
1.  chiudere l'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], se è in esecuzione.  
  
2.  Aggiungere un file denominato MBConsumer \\Dsl\\Custom cs e impostarne il contenuto al seguente.  
  
    ```  
  
    namespace Company.MB2Consume  
    {  
      using Microsoft.VisualStudio.Modeling.Integration;  
      using Company.MB3Provider;  
  
      public partial class ExampleShape  
      {  
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)  
        {  
          base.OnDoubleClick(e);  
          ExampleElement element = this.ModelElement as ExampleElement;  
          if (element.MBR != null)  
          {  
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;  
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))  
            {  
              Task task = adapter.ResolveElementReference<Task>(element.MBR);  
              // Open a window on this model:  
              ModelBusView view = adapter.GetDefaultView();  
              view.Show();  
              view.SetSelection(element.MBR);  
            }  
          }  
        }  
      }  
    }  
  
    ```  
  
3.  Premere CTRL\+F5.  
  
4.  Nell'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]aprire,  `Debugging\Sample.consume`.  
  
5.  Fare doppio clic su una forma.  
  
     Se si configura il MBR su tale elemento, il modello a cui si fa riferimento viene aperto e l'elemento a cui si fa riferimento è selezionato.  
  
## Vedere anche  
 [L'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)