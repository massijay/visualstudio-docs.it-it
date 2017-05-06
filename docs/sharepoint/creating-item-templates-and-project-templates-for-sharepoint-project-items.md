---
title: "Creating Item Templates and Project Templates for SharePoint Project Items"
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
  - "SharePoint project items, creating custom templates"
  - ".spdata files"
  - "projects [SharePoint development in Visual Studio], creating custom templates"
  - "SharePoint projects, creating custom templates"
  - "SharePoint development in Visual Studio, creating custom project and item templates"
  - "project items [SharePoint development in Visual Studio], creating custom templates"
ms.assetid: c95b5e35-76c4-4f0a-b645-0467ae683659
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Creating Item Templates and Project Templates for SharePoint Project Items
  Quando si definisce un tipo di elemento di progetto SharePoint personalizzato, è possibile associarlo a un modello di elemento o a un modello di progetto in modo che altri sviluppatori possano utilizzare l'elemento di progetto in Visual Studio.  È inoltre possibile creare una procedura guidata per il modello.  
  
 Ad esempio, Visual Studio non include un modello di progetto o un modello di elemento per l'aggiunta di un campo a un sito di SharePoint.  È possibile definire un tipo di elemento di progetto SharePoint che rappresenti un campo, quindi costruire un modello di elemento utilizzabile da altri sviluppatori per aggiungere l'elemento campo a un progetto SharePoint.  In alternativa, è possibile creare un modello di progetto in modo che gli sviluppatori possano creare un nuovo progetto SharePoint contenente l'elemento del campo. In entrambi i casi, è possibile fornire una procedura guidata visualizzata quando gli sviluppatori utilizzano il modello.  La procedura guidata può essere utilizzata per raccogliere informazioni dagli sviluppatori per la configurazione del nuovo elemento o progetto.  
  
 I modelli di elemento e di progetto sono file con estensione zip che contengono i file utilizzati da Visual Studio per creare un elemento di progetto o un progetto.  Per ulteriori informazioni sui principi fondamentali dei modelli di elemento e di progetto, vedere [Creazione di un progetto e di modelli di elemento personalizzati in Visual Studio](../ide/creating-project-and-item-templates.md).  
  
##  <a name="creatingitemtemplates"></a> Creazione di modelli di elementi  
 Quando si crea un modello di elemento per un elemento di progetto SharePoint, esistono alcuni file che sono sempre necessari e alcuni file facoltativi che possono essere utilizzati da determinati tipi di elementi di progetto.  Per una procedura dettagliata in cui viene illustrato come definire un tipo di elemento di progetto SharePoint e creare un modello di elemento a esso associato, vedere [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Nella tabella seguente sono elencati i file necessari per creare un modello di elemento per un elemento di progetto SharePoint.  
  
|File necessario|Descrizione|  
|---------------------|-----------------|  
|Un file con estensione spdata|Si tratta di un file XML che specifica il contenuto e il comportamento predefinito dell'elemento di progetto.  Questo file deve essere incluso nel modello di elemento.  Per ulteriori informazioni sul contenuto dei file spdata, vedere [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).|  
|Un file vstemplate.|Questo file fornisce a Visual Studio le informazioni necessarie per visualizzare il modello nella finestra di dialogo **Aggiungi nuovo elemento** e per creare dal modello un elemento di progetto.  Questo file deve essere incluso nel modello di elemento.  Per ulteriori informazioni, vedere [NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/it-it/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Un assembly di estensione Visual Studio che implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.|Questo assembly definisce il comportamento in fase di esecuzione dell'elemento di progetto.  Questo assembly deve essere incluso nel pacchetto VSIX con il modello di elemento.  Per ulteriori informazioni, vedere [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md) e [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|  
  
 Nella tabella seguente sono elencati alcuni dei file facoltativi più comuni che possono essere inclusi nel modello di elemento.  Alcuni tipi di elementi di progetto potrebbero richiedere altri file non elencati qui.  
  
|File facoltativo|Descrizione|  
|----------------------|-----------------|  
|Elements.xml|File di *elemento della funzionalità*.  Questo file definisce l'interfaccia utente e il comportamento della personalizzazione creata dall'elemento di progetto.  Ogni tipo di personalizzazione, ad esempio istanze di elenco, tipi di contenuto o azioni personalizzate, presenta uno schema diverso che definisce il contenuto di questo file.  Per ulteriori informazioni, vedere [Blocco predefinito: funzionalità](http://go.microsoft.com/fwlink/?LinkId=169183) e [Schemi di funzionalità](http://go.microsoft.com/fwlink/?LinkId=169192) \(le pagine potrebbero essere in inglese\).|  
|Schema.xml|File di schema per le definizioni di elenco.  Per ulteriori informazioni, vedere [Blocco predefinito: elenchi e raccolte documenti](http://msdn.microsoft.com/it-it/library/ee534985(office.14).aspx) e [Schema.xml](http://msdn.microsoft.com/it-it/library/ms459356(office.14).aspx) \(le pagine potrebbero essere in inglese\).|  
|WEBPART|File di *definizione della Web part*.  Questo file contiene le impostazioni delle proprietà di una Web part.  Per ulteriori informazioni, vedere [Blocco predefinito: Web part](http://msdn.microsoft.com/it-it/library/ee535520(office.14).aspx) \(la pagina potrebbe essere in inglese\).|  
|ASCX|File UserControl di ASP.NET.  Questo file definisce l'interfaccia utente di una Web part visiva.|  
|ASPX|File di paging ASP.NET.  Questo file contiene il markup XML che definisce una pagina di applicazione.|  
|CS o VB|Questi file di codice definiscono il comportamento delle personalizzazioni di SharePoint che dispongono di un modello di programmazione accessibile tramite il codice Visual C\# o Visual Basic, ad esempio pagine di applicazione, Web part e flussi di lavoro.|  
  
## Creazione di modelli di progetto  
 Quando si crea un modello di progetto SharePoint, esistono alcuni file che sono sempre necessari e alcuni file facoltativi che possono essere utilizzati da determinati tipi di progetto.  In genere, i progetti SharePoint includono almeno un elemento di progetto SharePoint.  Tuttavia non si tratta di un elemento necessario.  È ad esempio possibile definire un modello di progetto SharePoint utilizzabile solo per distribuire soluzioni SharePoint create in altri progetti.  
  
 Per una procedura dettagliata in cui viene illustrato come definire un tipo di elemento di progetto SharePoint e creare un modello di progetto a esso associato, vedere [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Nella tabella riportata di seguito sono elencati i file che devono essere inclusi in un modello di progetto SharePoint.  
  
|File necessario|Descrizione|  
|---------------------|-----------------|  
|Un file con estensione vstemplate.|Questo file fornisce a Visual Studio le informazioni necessarie per visualizzare il modello nella finestra di dialogo **Nuovo progetto** e per creare dal modello un progetto.  Per ulteriori informazioni, vedere [NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/it-it/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Un file con estensione csproj o vbproj|Si tratta del file di progetto.  Consente di definire il contenuto e le impostazioni di configurazione del progetto.|  
|Package.package|Questo file definisce il pacchetto di distribuzione per il progetto.  Quando si utilizza Progettazione pacchetti per personalizzare il pacchetto della soluzione per il progetto, i dati sul pacchetto della soluzione vengono archiviati all'interno di questo file in Visual Studio.<br /><br /> Quando si crea un modello di progetto SharePoint personalizzato, è consigliabile includere solo il contenuto obbligatorio minimo nel file Package.package e configurare il pacchetto della soluzione tramite le API dello spazio dei nomi <xref:Microsoft.VisualStudio.SharePoint.Packages> in un'estensione associata al modello di progetto.  Se si esegue questa operazione, il modello di progetto viene protetto da modifiche future alla struttura del file Package.package.  Per un esempio in cui viene illustrato come creare un file Package.package che include solo il contenuto obbligatorio minimo, vedere [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Se si desidera modificare direttamente il file Package.package, è possibile verificare il contenuto tramite lo schema nel percorso %Programmi \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\PackageModelSchema.xsd.|  
|Package.Template.xml|Questo file costituisce la base per il file manifesto della soluzione \(manifest.xml\) per il pacchetto della soluzione SharePoint \(con estensione wsp\) generato dal progetto.  È possibile aggiungere contenuto a tale file se si desidera specificare un comportamento che non deve essere modificato dagli utenti del tipo di progetto in uso.  Per ulteriori informazioni, vedere [Blocco predefinito: soluzioni](http://msdn.microsoft.com/it-it/library/ee537008(office.14).aspx) e [Schema della soluzione](http://msdn.microsoft.com/it-it/library/ms442108(office.14).aspx) \(le pagine potrebbero essere in inglese\).<br /><br /> Quando si compila un pacchetto di soluzione dal progetto, in Visual Studio il contenuto dei file Package.package e Package.Template.xml viene unito nel file manifesto della soluzione.  Per ulteriori informazioni sulla compilazione dei pacchetti di soluzioni, vedere [How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/it-it/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
 Nella tabella riportata di seguito sono elencati i file facoltativi che possono essere inclusi nel modello di progetto.  
  
|File facoltativo|Descrizione|  
|----------------------|-----------------|  
|Elementi di progetto SharePoint|È possibile includere uno o più file con estensione spdata che definiscano i tipi di elemento di progetto SharePoint.  Ogni file con estensione spdata deve disporre di un'implementazione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> corrispondente in un assembly di estensioni incluso nel pacchetto VSIX con il modello di progetto.  Per ulteriori informazioni, vedere [Creazione di modelli di elemento](#creatingitemtemplates).<br /><br /> In genere, i progetti SharePoint includono almeno un elemento di progetto SharePoint.  Tuttavia non si tratta di un elemento necessario.|  
|*NomeFunzionalità*.feature|Questo file definisce una funzionalità SharePoint utilizzata per raggruppare diversi elementi di progetto per la distribuzione.  Quando si utilizza Progettazione funzionalità per personalizzare una funzionalità nel progetto, i dati sulla funzionalità vengono archiviati all'interno di questo file in Visual Studio.  Se si desidera raggruppare gli elementi di progetto in funzionalità differenti, è possibile includere più file con estensione feature.<br /><br /> Quando si crea un modello di progetto SharePoint personalizzato, è consigliabile includere solo il contenuto obbligatorio minimo in ogni file con estensione feature e configurare le funzionalità tramite le API dello spazio dei nomi <xref:Microsoft.VisualStudio.SharePoint.Features> in un'estensione associata al modello di progetto.  Se si esegue questa operazione, il modello di progetto viene protetto da modifiche future alla struttura del file con estensione feature.  Per un esempio in cui viene illustrato come creare un file con estensione feature che include solo il contenuto obbligatorio minimo, vedere [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Se si desidera modificare direttamente un file con estensione feature, è possibile verificare il contenuto tramite lo schema nel percorso %Programmi \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\FeatureModelSchema.xsd.|  
|*NomeFunzionalità*.Template.xml|Questo file costituisce la base per il file manifesto della funzionalità \(Feature.xml\) per ogni funzionalità generata dal progetto.  È possibile aggiungere contenuto a tale file se si desidera specificare un comportamento che non deve essere modificato dagli utenti del tipo di progetto in uso.  Per ulteriori informazioni, vedere [Blocco predefinito: funzionalità](http://msdn.microsoft.com/it-it/library/ee537350(office.14).aspx) e [File Feature.xml](http://msdn.microsoft.com/it-it/library/ms475601(office.14).aspx) \(le pagine potrebbero essere in inglese\).<br /><br /> Quando si compila un pacchetto di soluzione dal progetto, in Visual Studio il contenuto di ogni coppia di file *NomeFunzionalità*.feature e *NomeFunzionalità*.Template.xml viene unito in un file manifesto di funzionalità.  Per ulteriori informazioni sulla compilazione dei pacchetti di soluzioni, vedere [How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/it-it/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
## Creazione di procedure guidate per i modelli di elemento e di progetto  
 Dopo aver definito un tipo di elemento di progetto SharePoint e averlo associato a un modello di elemento o di progetto, è anche possibile creare una procedura guidata.  Nella procedura guidata viene visualizzato quando uno sviluppatore utilizza il modello di elemento per aggiungere l'elemento di progetto SharePoint a un progetto oppure quando un sviluppatore utilizza il modello di progetto per creare un nuovo progetto contenente l'elemento di progetto SharePoint.  La procedura guidata può essere utilizzata per raccogliere informazioni dagli sviluppatori e inizializzare il nuovo elemento di progetto SharePoint.  
  
 Per le procedure dettagliate in cui viene illustrato come creare procedure guidate per i modelli di elemento e di progetto, vedere [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) e [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## Vedere anche  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati in Visual Studio](../ide/creating-project-and-item-templates.md)  
  
  