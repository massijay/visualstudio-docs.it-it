---
title: "Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SafeControlEntries"
  - "VS.SharePointTools.Project.ProjectOutputReference"
  - "VS.SharePointTools.Project.FeatureProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "proprietà della funzionalità [sviluppo per SharePoint in Visual Studio]"
  - "ricevitore di funzionalità [sviluppo per SharePoint in Visual Studio]"
  - "riferimenti all'output del progetto [sviluppo per SharePoint in Visual Studio]"
  - "controlli sicuri [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, strumenti di creazione di pacchetti avanzati"
  - "sviluppo per SharePoint in Visual Studio, proprietà funzionalità"
  - "sviluppo per SharePoint in Visual Studio, ricevitore di funzionalità"
  - "sviluppo per SharePoint in Visual Studio, riferimenti all'output del progetto"
  - "sviluppo per SharePoint in Visual Studio, controlli sicuri"
ms.assetid: 209ff3b9-d701-4d27-9d24-005fcc811cbe
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto
  Tutti gli elementi di progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] includono proprietà utilizzabili per specificare ulteriori dati quando il progetto viene distribuito in SharePoint.  Di seguito sono riportate le proprietà:  
  
-   Proprietà funzionalità  
  
-   Ricevitori di funzionalità  
  
-   Riferimenti all'output del progetto  
  
-   Voci di controllo sicure  
  
 Tali proprietà vengono visualizzate nella finestra **Proprietà**.  
  
## Proprietà funzionalità  
 Utilizzare la proprietà **Proprietà funzionalità** per specificare i dati utilizzati nella funzionalità.  I dati delle proprietà della funzionalità sono un set di valori, archiviato come coppie chiave\/valore, che viene incluso in una funzionalità quando viene distribuita in SharePoint.  Dopo aver distribuito la funzionalità, è possibile accedere ai valori della proprietà nel codice.  
  
 Quando si aggiunge il valore di una proprietà della funzionalità a un elemento del progetto, tale valore viene aggiunto come elemento nel manifesto della funzionalità dell'elemento.  In un progetto del modello di applicazione integrativa dei dati, ad esempio, la proprietà della funzionalità ModelFileName viene visualizzata nel modo seguente:  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Dopo avere impostato un valore per la proprietà della funzionalità, tale valore viene aggiunto come elemento FeatureProperty nel file con estensione spdata del progetto.  Per informazioni sull'accesso alle proprietà di SharePoint, vedere [Classe SPFeaturePropertyCollection](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 I valori di proprietà di funzionalità identici per tutti gli elementi del progetto vengono uniti nel manifesto della funzionalità.  Se, tuttavia, due elementi del progetto diversi specificano la stessa chiave di proprietà della funzionalità con valori non corrispondenti, si verifica un errore di convalida.  
  
 Per aggiungere direttamente proprietà della funzionalità al file della funzionalità \(\*.feature\), chiamare il metodo del modello a oggetti SharePoint di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>.  Se si utilizza questo metodo, tenere presente che la stessa regola relativa all'aggiunta di valori di proprietà di funzionalità identici nelle proprietà della funzionalità viene applicata anche alle proprietà aggiunte direttamente al file della funzionalità.  
  
## Ricevitore di funzionalità  
 I ricevitori di funzionalità sono costituiti da codice eseguito quando si verificano determinati eventi in una funzionalità contenitore dell'elemento del progetto.  È, ad esempio, possibile definire ricevitori di funzionalità da eseguire quando la funzionalità viene installata, attivata o aggiornata.  È disponibile un metodo per l'aggiunta diretta di un ricevitore di funzionalità in una funzionalità, come descritto in [Procedura dettagliata: aggiungere ricevitori di eventi di funzionalità](../sharepoint/walkthrough-add-feature-event-receivers.md).  In alternativa, è possibile fare riferimento a un nome di classe e a un assembly del ricevitore di funzionalità nella proprietà **Ricevitore di funzionalità**.  
  
### Metodo diretto  
 Quando si aggiunge un ricevitore di funzionalità direttamente a una funzionalità, nel nodo **Funzionalità** di Esplora soluzioni viene inserito un file di codice.  Quando si compila la soluzione SharePoint, il codice viene compilato in un assembly e distribuito in SharePoint.  Per impostazione predefinita, le proprietà della funzionalità **Assembly ricevitore** e **Classe ricevitore** fanno riferimento al nome della classe e all'assembly.  
  
### Metodo di riferimento  
 Un altro modo per aggiungere un ricevitore di funzionalità consiste nell'utilizzare la proprietà **Ricevitore di funzionalità** di un elemento del progetto per fare riferimento a un assembly del ricevitore di funzionalità.  Il valore della proprietà Ricevitore di funzionalità presenta due sottoproprietà, **Assembly** e **Nome classe**.  L'assembly deve utilizzare il proprio nome sicuro completo, mentre il nome della classe deve corrispondere al nome del tipo completo.  Per ulteriori informazioni, vedere [Assembly con nome sicuro](http://go.microsoft.com/fwlink/?LinkID=169573).  Dopo avere distribuito la soluzione in SharePoint, la funzionalità utilizzerà il ricevitore di funzionalità di riferimento per gestire gli eventi di funzionalità.  
  
 Durante la compilazione della soluzione, i valori di proprietà del ricevitore di funzionalità nella funzionalità e nei relativi progetti vengono uniti per impostare gli attributi ReceiverAssembly e ReceiverClass dell'elemento Feature nel manifesto della funzionalità del file di soluzione di SharePoint \(con estensione wsp\).  Se, pertanto, si specificano entrambi i valori delle proprietà Assembly e Nome classe di un elemento del progetto e di una funzionalità, tali valori devono corrispondere.  Se i valori non corrispondono, verrà visualizzato un errore di convalida.  Se si desidera che un elemento del progetto faccia riferimento a un assembly del ricevitore di funzionalità diverso da quello utilizzato dalla relativa funzionalità, spostarlo in un'altra funzionalità.  
  
 Se si fa riferimento a un assembly del ricevitore di funzionalità che non è già presente nel server, è inoltre necessario includere il file di assembly nel pacchetto perché non verrà aggiunto automaticamente in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Quando si distribuisce la funzionalità, il file di assembly viene copiato nella [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] del sistema o nella cartella Bin della directory fisica di SharePoint.  Per ulteriori informazioni, vedere [Procedura: Aggiungere e rimuovere assembly aggiuntivi](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Per ulteriori informazioni sui ricevitori di funzionalità, vedere [Ricevitore di eventi di funzionalità](http://go.microsoft.com/fwlink/?LinkID=169574) ed [Eventi di funzionalità](http://go.microsoft.com/fwlink/?LinkID=169575).  
  
## Riferimenti all'output del progetto  
 La proprietà Riferimenti all'output del progetto specifica una dipendenza, ad esempio un assembly, che l'elemento del progetto deve eseguire.  Si supponga, ad esempio, che la soluzione includa un progetto di integrazione applicativa dei dati e un progetto di classe.  Se il progetto di integrazione applicativa dei dati presenta una dipendenza dall'assembly generata dal progetto di classe, è possibile fare riferimento all'assembly nella proprietà "Riferimenti all'output del progetto" del progetto di integrazione applicativa dei dati.  Quando tale progetto viene compresso, l'assembly dipendente viene incluso nel pacchetto.  
  
 I riferimenti all'output del progetto sono in genere assembly ma in alcuni casi, ad esempio con i progetti Silverlight, possono essere altri tipi di file.  
  
 Per ulteriori informazioni, vedere [Procedura: aggiungere un riferimento all'output del progetto](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## Voci di controllo sicure  
 SharePoint offre un meccanismo di sicurezza, denominato voci di controllo sicure, per limitare l'accesso degli utenti non attendibili a determinati controlli.  In base alla progettazione, SharePoint consente a utenti non attendibili di caricare e creare pagine ASPX sul server SharePoint.  Per impedire a tali utenti l'aggiunta di codice unsafe alle pagine ASPX, in SharePoint l'accesso ai *controlli sicuri* è limitato.  I controlli sicuri sono Web part e controlli ASPX definiti come sicuri e utilizzabili da qualsiasi utente nel sito.  Per ulteriori informazioni, vedere [Passaggio 4: Aggiungere la Web part all'elenco sicuro dei comandi](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Ogni elemento di progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ha una proprietà chiamata **Voci di controllo sicure** che presenta due sottoproprietà booleane: **Safe** e **Safe Against Script**.  La proprietà Safe consente di specificare se gli utenti non attendibili possono accedere a un controllo.  La proprietà Sicurezza script specifica se gli utenti non attendibili possono visualizzare e modificare le proprietà di un controllo.  
  
 Alle voci di controllo sicure viene fatto riferimento in base all'assembly.  Per aggiungere voci di controllo sicure all'assembly di un progetto è necessario immetterle nella proprietà **Voci di controllo sicure** dell'elemento del progetto.  È tuttavia possibile aggiungere voci di controllo sicure all'assembly di un progetto anche tramite la scheda **Avanzate** in **Progettazione pacchetti** quando si aggiunge un assembly aggiuntivo al pacchetto.  Per ulteriori informazioni, vedere [Procedura: contrassegnare i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md) o [Registrazione di un assembly Web part come controllo sicuro](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### Voci XML per i controlli sicuri  
 Quando si aggiunge una voce di controllo sicura a un elemento del progetto o all'assembly del progetto, viene scritto un riferimento nel manifesto di pacchetto nel formato seguente:  
  
```  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Utilizzo di moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  