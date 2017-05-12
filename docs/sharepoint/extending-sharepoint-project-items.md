---
title: "Extending SharePoint Project Items"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Extending SharePoint Project Items
  Creare un'estensione dell'elemento di progetto quando si desidera aggiungere funzionalità a un tipo di elemento di progetto SharePoint già installato in Visual Studio.  Ad esempio, è possibile creare un'estensione per gli elementi di progetto incorporati **Ricevitore di eventi** o **Definizione di elenco** in Visual Studio oppure creare un'estensione per un tipo di elemento di progetto personalizzato.  È inoltre possibile creare un'estensione per tutti i tipi di elementi di progetto SharePoint.  
  
## Attività per l'estensione di elementi di progetto SharePoint  
 Per estendere un elemento di progetto, compilare un assembly di Visual Studio Extension che implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  Per ulteriori informazioni, vedere [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Quando si estende un elemento di progetto personalizzato, è possibile aggiungervi la seguente funzionalità.  
  
-   Aggiungere una voce di menu di scelta rapida a un elemento di progetto.  La voce di menu viene visualizzata quando si apre il menu di scelta rapida per l'elemento di progetto in **Esplora soluzioni**.  Aprire il menu di scelta rapida fare clic con il pulsante destro del mouse sull'elemento di progetto o scegliendolo e scegliendo lo spostamento \+ chiavi F10.  Per ulteriori informazioni, vedere [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
-   Aggiungere una proprietà personalizzata all'elemento di progetto.  La proprietà viene visualizzata nella finestra **Proprietà** quando si seleziona l'elemento di progetto in **Esplora soluzioni**.  Per ulteriori informazioni, vedere [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
 Per una procedura dettagliata in cui viene illustrato come creare, distribuire e testare un'estensione dell'elemento di progetto, vedere [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## Informazioni sulla relazione tra estensioni di elementi di progetto e istanze di elementi di progetto  
 Quando si crea un'estensione di elemento di progetto SharePoint, l'estensione viene caricata in Visual Studio quando un elemento di progetto del tipo associato viene aggiunto a un progetto SharePoint.  Ad esempio, se si crea un'estensione per gli elementi di progetto **Ricevitore di eventi**, l'estensione viene caricata in Visual Studio quando un utente aggiunge un elemento di progetto **Ricevitore di eventi** a un progetto.  In Visual Studio viene utilizzata la stessa istanza dell'estensione per tutte le istanze del tipo di elemento di progetto associato.  Nell'esempio precedente se l'utente aggiunge al progetto un secondo elemento di progetto **Ricevitore di eventi**, per personalizzare il secondo elemento di progetto verrà utilizzata la stessa istanza dell'estensione.  
  
 Per accedere a una specifica istanza del tipo di elemento di progetto in fase di estensione, gestire uno degli eventi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> del parametro *projectItemType* nell'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>.  Ad esempio per determinare quando un elemento di progetto del tipo in fase di estensione viene aggiunto a un progetto, gestire l'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>.  Per ulteriori informazioni, vedere [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## Identificatori per gli elementi di progetto SharePoint  
 Ogni elemento di progetto SharePoint dispone di un identificatore di stringa corrispondente.  È necessario conoscere l'identificatore per un elemento di progetto se si desidera effettuare le attività seguenti:  
  
-   Creazione di un'estensione per l'elemento di progetto.  In questo caso, è necessario passare l'identificatore per l'elemento di progetto che si desidera estendere al costruttore di <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Per creare un'estensione per ogni tipo di elemento di progetto, passare il valore stringa **\***.  
  
-   Aggiunta a livello di codice dell'elemento di progetto a un progetto.  In questo caso, è necessario passare l'identificatore per l'elemento di progetto al metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A>.  
  
 Nella tabella seguente sono elencati gli identificatori per gli elementi di progetto SharePoint inclusi in Visual Studio.  
  
|Nome dell'elemento di progetto|Identificatore di stringa|  
|------------------------------------|-------------------------------|  
|Modello di Catalogo dati business|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Tipo di contenuto|Microsoft.VisualStudio.SharePoint.ContentType|  
|Ricevitore di eventi|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Elemento vuoto|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Definizione di elenco<br /><br /> Definizione di elenco da tipo di contenuto|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Istanza di elenco|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Modulo|Microsoft.VisualStudio.SharePoint.Module|  
|Flusso di lavoro sequenziale<br /><br /> Flusso di lavoro macchina a stati|Microsoft.VisualStudio.SharePoint.Workflow|  
|Definizione di sito|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Web part visiva|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web part|Microsoft.VisualStudio.SharePoint.WebPart|  
|Form di associazione flusso di lavoro|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## Vedere anche  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  