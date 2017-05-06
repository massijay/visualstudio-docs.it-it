---
title: "Deploying Extensions for the SharePoint Tools in Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, deploying extensions"
ms.assetid: 69927d95-acdf-4fd8-ac43-28e9a7fa8a38
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Deploying Extensions for the SharePoint Tools in Visual Studio
  Per distribuire un'estensione degli strumenti di SharePoint, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) contenente l'assembly di estensioni e qualsiasi altro file che si desidera distribuire con l'estensione.  Un pacchetto VSIX è un file compresso conforme allo standard Open Packaging Conventions \(OPC\).  I pacchetti VSIX sono indicati con l'estensione vsix.  
  
 Una volta creato un pacchetto VSIX, altri utenti potranno eseguire il file vsix per installare l'estensione.  Quando un utente installa l'estensione, tutti i file vengono installati nella cartella %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions.  Per distribuire l'estensione, è possibile caricare il pacchetto VSIX nel sito Web [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) \(la pagina potrebbe essere in inglese\) o distribuire il pacchetto ai clienti tramite altri mezzi, ad esempio ospitando il pacchetto in una condivisione di rete o in un altro sito Web.  
  
 Per ulteriori informazioni sulla creazione di pacchetti VSIX e sulla relativa distribuzione in [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) \(la pagina potrebbe essere in inglese\), vedere [Distribuzione di estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 È possibile creare un pacchetto VSIX tramite il modello **Progetto VSIX** in Visual Studio oppure manualmente.  
  
## Utilizzo di progetti VSIX per creare pacchetti VSIX  
 È possibile utilizzare il modello **Progetto VSIX** fornito da Visual Studio SDK per creare pacchetti VSIX per le estensioni degli strumenti di SharePoint.  L'utilizzo di un progetto VSIX offre diversi vantaggi rispetto alla creazione manuale di un pacchetto VSIX:  
  
-   In Visual Studio il pacchetto VSIX viene generato automaticamente quando si compila il progetto.  Attività quali l'aggiunta dei file di distribuzione al pacchetto e la creazione del file \[Content\_Types\].xml per il pacchetto vengono effettuate automaticamente.  
  
-   È possibile configurare il progetto VSIX in modo da includere nel pacchetto VSIX l'output di compilazione del progetto di estensione e altri file, ad esempio modelli di progetto e modelli di elemento.  
  
 Per ulteriori informazioni sull'utilizzo di un progetto VSIX, vedere [Modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
### Organizzazione dei progetti  
 Per impostazione predefinita, i progetti VSIX generano solo pacchetti VSIX, non assembly.  Di conseguenza, generalmente non si implementano estensioni degli strumenti di SharePoint in un progetto VSIX.  Di solito si utilizzano almeno due progetti:  
  
-   Un progetto VSIX.  
  
-   Un progetto libreria di classi che implementa l'estensione.  
  
 È inoltre possibile utilizzare ulteriori progetti per determinati tipi di estensioni:  
  
-   Un progetto libreria di classi che implementa tutti i comandi di SharePoint utilizzati dall'estensione.  Per una procedura dettagliata dove viene illustrato questo scenario, vedere [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Un progetto che crea un modello di elemento o un modello di progetto se l'estensione definisce un nuovo tipo di elemento di SharePoint.  Per una procedura dettagliata dove viene illustrato questo scenario, vedere [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
-   Un progetto libreria di classi che implementa una procedura guidata personalizzata per un modello di elemento o un modello di progetto se l'estensione include un modello.  Per una procedura dettagliata dove viene illustrato questo scenario, vedere [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
 Se si includono tutti i progetti nella stessa soluzione di Visual Studio, è possibile modificare il file source.extension.vsixmanifest nel progetto VSIX in modo da includere l'output di compilazione dei progetti Libreria di classi.  
  
### Modifica del manifesto VSIX  
 È necessario modificare il file source.extension.vsixmanifest nel progetto VSIX per includere voci per tutti gli elementi che si desidera includere nell'estensione.  Quando si apre il file source.extension.vsixmanifest dal menu di scelta rapida, il file viene visualizzato in una finestra di progettazione che fornisce un'interfaccia utente per modificare l'xml nel file.  Per ulteriori informazioni, vedere [Progettazione del manifesto VSIX](../extensibility/media/vsix-manifest-designer.png).  
  
 È necessario aggiungere voci al file source.extension.vsixmanifest per gli elementi seguenti:  
  
-   Assembly dell'estensione.  
  
-   L'assembly che implementa tutti i comandi di SharePoint utilizzati dall'estensione.  
  
-   Qualsiasi modello di progetto o modello di elemento associato all'estensione.  
  
-   Una procedura guidata personalizzata per un modello associato all'estensione.  
  
 Le procedure seguenti descrivono come aggiungere voci al file vsixmanifest per ciascuno di questi elementi.  
  
##### Per includere l'assembly di estensioni  
  
1.  Nel progetto VSIX, aprire il menu di scelta rapida per il file source.extension.vsixmanifest quindi scegliere **Apri**.  
  
     Il file verrà aperto nella finestra di progettazione  
  
2.  Nella scheda **Asset** dell'editor, scegliere il pulsante **Nuova**.  
  
     La finestra di dialogo **Aggiungi nuovo asset** viene aperto.  
  
3.  Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.MefComponent**.  
  
4.  Nell'elenco **Alimentazione**, eseguire una delle operazioni seguenti:  
  
    -   Se l'assembly di estensioni è compilato da un progetto incluso nella stessa soluzione del progetto VSIX, scegliere **Progetto nella soluzione corrente**.  Nell'elenco **Project**, scegliere il nome del progetto.  
  
    -   Se l'assembly di estensioni è incluso come file nel progetto, scegliere **File in filesystem**.  Nell'elenco **Percorso**, immettere il percorso completo del file di assembly di estensioni, o utilizzare il pulsante **Sfoglia** per individuare e selezionare il file di assembly.  
  
5.  Scegliere il pulsante **OK**.  
  
##### Per includere un assembly di comandi di SharePoint  
  
1.  Nel progetto VSIX, aprire il menu di scelta rapida per il file source.extension.vsixmanifest quindi scegliere il pulsante **Apri**.  
  
     Il file verrà aperto nella finestra di progettazione.  
  
2.  Nella sezione **Asset** dell'editor, scegliere il pulsante **Nuova**.  
  
     La finestra di dialogo **Aggiungi nuovo asset** viene aperto.  
  
3.  Nella casella **Tipo**, immettere **SharePoint.Commands.v4**.  
  
4.  Nell'elenco **Alimentazione**, eseguire una delle operazioni seguenti:  
  
    -   Se l'assembly di comandi è compilato da un progetto incluso nella stessa soluzione del progetto VSIX, scegliere **Progetto nella soluzione corrente**.  Nell'elenco **Project**, scegliere il nome del progetto.  
  
    -   Se l'assembly di comandi è incluso come file nel progetto, scegliere **File in filesystem**.  Nell'elenco **Percorso**, immettere il percorso completo del file di assembly di estensioni, o utilizzare il pulsante **Sfoglia** per individuare e selezionare il file di assembly.  
  
5.  Scegliere il pulsante **OK**.  
  
##### Per includere un modello creato  
  
1.  Nel progetto VSIX, aprire il menu di scelta rapida per il file source.extension.vsixmanifest quindi scegliere il pulsante **Apri**.  
  
     Il file verrà aperto nella finestra di progettazione.  
  
2.  Nella sezione **Asset** dell'editor, scegliere il pulsante **Nuova**.  
  
     La finestra di dialogo **Aggiungi nuovo asset** viene aperto.  
  
3.  Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.ProjectTemplate** o **Microsoft.VisualStudio.ItemTemplate**.  
  
4.  Nell'elenco **Alimentazione**, scegliere **Progetto nella soluzione corrente**.  
  
5.  Nell'elenco **Project**, scegliere il nome del progetto e quindi scegliere il pulsante **OK**.  
  
6.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto di modello di elemento o del modello di progetto e quindi scegliere **Scarica progetto**.  
  
7.  Aprire nuovamente il menu di scelta rapida del nodo di progetto e quindi scegliere **Modifica***YourTemplateProjectName***aprire** o **Modifica***YourTemplateProjectName***vbproj**.  
  
8.  Individuare l'elemento `VSTemplate` seguente nel file di progetto.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. Sostituire l'elemento con il codice XML seguente.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     L'elemento `OutputSubPath` specifica cartelle aggiuntive nel percorso in cui viene creato il modello di progetto quando si compila il progetto.  Le cartelle specificate garantiscono che il modello di elemento sarà disponibile solo quando i clienti aprire la finestra di dialogo **Aggiungi nuovo progetto**, espandere il nodo **SharePoint** quindi selezionare il nodo **2010**.  
  
10. Salvare e chiudere il file.  
  
11. In **Esplora soluzioni**, aprire il menu di scelta rapida del progetto di modello di elemento o del modello di progetto e quindi scegliere **Ricarica progetto**.  
  
##### Per includere un modello creato manualmente  
  
1.  Nel progetto VSIX aggiungere una nuova cartella al progetto che contiene il modello.  
  
2.  Sotto questa nuova cartella creare le sottocartelle seguenti, quindi aggiungere il file modello \(zip\) alla cartella *ID impostazioni locali*.  
  
     *CartellaModelliPersonalizzati*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *ID impostazioni locali*  
  
     *YourTemplateName*.zip  
  
     Ad esempio, se si dispone di un modello di elemento denominato ContosoCustomAction.zip che supporta le impostazioni locali Inglese \(Stati Uniti\), il percorso completo potrebbe essere ItemTemplates\\SharePoint\\SharePoint14\\1033\\ContosoCustomAction.zip.  
  
3.  In **Esplora soluzioni**, selezionare il file modello \(*YourTemplateName*zip\).  
  
4.  Nella finestra **Proprietà** impostare la proprietà **Operazione di compilazione** su **Contenuto**.  
  
5.  Aprire il menu di scelta rapida per il file source.extension.vsixmanifest quindi scegliere **Apri**.  
  
     Il file verrà aperto nella finestra di progettazione.  
  
6.  Nella sezione **Asset** dell'editor, scegliere il pulsante **Nuova**.  
  
     La finestra di dialogo **Aggiungi nuovo asset** viene aperto.  
  
7.  Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.ItemTemplate** o **Microsoft.VisualStudio.ProjectTemplate**.  
  
8.  Nell'elenco **Alimentazione**, scegliere **File in filesystem**.  
  
9. Nel campo **Percorso**, immettere il percorso completo dell'assembly, ad esempio **ItemTemplates \\ SharePoint \\ SharePoint14 \\ 1033 \\ ContosoCustomAction.zip**, o utilizzare il pulsante **Sfoglia** per individuare e selezionare l'assembly e quindi selezionare il pulsante **OK**.  
  
##### Per includere una procedura guidata per un modello di progetto o un modello di elemento  
  
1.  Nel progetto VSIX, aprire il menu di scelta rapida per il file source.extension.vsixmanifest quindi scegliere **Apri**.  
  
     Il file verrà aperto nella finestra di progettazione.  
  
2.  Nella sezione **Asset** dell'editor, scegliere il pulsante **Nuova**.  
  
     La finestra di dialogo **Aggiungi nuovo asset** viene aperto.  
  
3.  Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.Assembly**.  
  
4.  Nell'elenco **Alimentazione**, eseguire una delle operazioni seguenti:  
  
    -   Se l'assembly della procedura guidata è compilato da un progetto incluso nella stessa soluzione del progetto VSIX, scegliere **Progetto nella soluzione corrente**.  Nell'elenco **Project**, scegliere il nome del progetto.  
  
    -   Se l'assembly della procedura guidata è incluso come file nel progetto, scegliere **File in filesystem**.  Nel campo **Percorso**, immettere il percorso completo del file di assembly, oppure utilizzare il pulsante **Sfoglia** per individuare e selezionare l'assembly.  
  
5.  Scegliere il pulsante **OK**.  
  
### Procedure dettagliate correlate  
 Nella tabella riportata di seguito sono elencate le procedure dettagliate che illustrano come utilizzare un progetto VSIX per distribuire tipi diversi di estensioni degli strumenti di SharePoint.  
  
|Tipo di estensione|Procedure dettagliate correlate|  
|------------------------|-------------------------------------|  
|Un'estensione che comprende soltanto l'assembly dell'estensione|[Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|Un'estensione che comprende i comandi di SharePoint|[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|Un'estensione che comprende un modello di Visual Studio|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|Un'estensione che comprende una creazione guidata modelli|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## Creazione manuale di pacchetti VSIX  
 Se si desidera creare manualmente il pacchetto VSIX per l'estensione degli strumenti di SharePoint, effettuare i passaggi seguenti:  
  
1.  Creare il file extension.vsixmanifest, il file \[Content\_Types\].xml e il file del pacchetto VSIX \(file con estensione vsix\).  Per ulteriori informazioni, vedere [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md) e [Procedura: Creare manualmente il pacchetto di un'estensione &#40;distribuzione VSIX&#41;](~/misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
2.  Aggiungere l'assembly di estensioni al pacchetto VSIX.  Se l'estensione include un comando di SharePoint, aggiungere al pacchetto VSIX anche l'assembly che implementa il comando di SharePoint.  
  
3.  Modificare il file extension.vsixmanifest:  
  
    -   Aggiungere un elemento `Microsoft.VisualStudio.MefComponent` nell'elemento `Assets` quindi impostare il valore del nuovo elemento sul percorso relativo dell'assembly che implementa l'estensione nel pacchetto VSIX.  Per ulteriori informazioni, vedere [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/it-it/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
    -   Se l'estensione include un comando di SharePoint che effettua chiamate nel modello a oggetti del server di SharePoint, aggiungere un elemento `Microsoft.VisualStudio.Assembly` nell'elemento `Assets`.  Impostare il valore del nuovo elemento sul percorso relativo dell'assembly che implementa il comando di SharePoint nel pacchetto VSIX.  Per ulteriori informazioni, vedere [Elemento di risorsa \(schema VSX\)](http://msdn.microsoft.com/it-it/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
    -   Se l'estensione include un modello di progetto o un modello di elemento, aggiungere un elemento `ItemTemplate` o `ProjectTemplate` nell'elemento `Assets`.  Impostare il valore del nuovo elemento sul percorso relativo della cartella che contiene il modello nel pacchetto VSIX.  Per ulteriori informazioni, vedere [NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/it-it/87add64c-9dcd-495f-8815-209dab182cb1) e [NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/it-it/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
    -   Se l'estensione include una procedura guidata personalizzata per un modello di progetto o un modello di elemento, aggiungere un elemento `Assembly` nell'elemento `Assets`.  Impostare il valore del nuovo elemento sul percorso relativo dell'assembly nel pacchetto VSIX e impostare l'attributo `AssemblyName` al nome completo dell'assembly \(inclusa la versione, impostazioni cultura e token di chiave pubblica.  Per ulteriori informazioni, vedere [Elemento di dipendenza \(schema VSX\)](http://msdn.microsoft.com/it-it/1f63f60a-98ad-48ec-8e44-4eba383d3e37).  
  
### Esempio  
 Il seguente esempio mostra il contenuto di un file extension.vsixmanifest per un'estensione degli strumenti di SharePoint.  L'estensione viene distribuita in un assembly denominato Contoso.ProjectExtension.dll.  L'estensione include un assembly di comandi di SharePoint denominato Contoso.ExtensionCommands.dll e un modello di elemento in una cartella denominata **ItemTemplates** nel pacchetto VSIX.  In questo esempio si presuppone che entrambi gli assembly siano nella stessa cartella del file extension.vsixmanifest nel pacchetto VSIX.  
  
```  
<PackageManifest Version=”2.0.0” xmlns=”http://schemas.microsoft.com/developer/vsx-schema/2011”>  
  <Metadata>  
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />  
    <DisplayName>CustomActionProjectItem</DisplayName>  
    <Description>Empty VSIX Project.</Description>  
  </Metadata>  
  <Installation>  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />  
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />  
  </Assets>  
</PackageManifest>  
  
```  
  
## Vedere anche  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  