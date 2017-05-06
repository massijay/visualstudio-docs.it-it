---
title: "Extending SharePoint Projects"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 4643012b-6e6c-4b7c-bb92-b04b34f6c715
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Projects
  Quando si desidera personalizzare le funzionalità a livello di progetto dei progetti SharePoint, è possibile creare un'estensione di progetto.  Ad esempio, è possibile aggiungere proprietà del progetto personalizzate o rispondere a eventi a livello di progetto generati quando l'utente sviluppa una soluzione SharePoint in Visual Studio.  
  
## Creazione di estensioni di progetto  
 Per estendere un elemento del progetto, compilare un assembly di Visual Studio Extension che implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Per ulteriori informazioni, vedere [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Quando si crea un'estensione di progetto, è inoltre possibile aggiungere la funzionalità seguente ai progetti SharePoint:  
  
-   Aggiungere una voce di menu di scelta rapida.  La voce di menu viene visualizzata quando si apre il menu di scelta rapida per un nodo del progetto SharePoint in **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo o scegliendolo e scegliendo lo spostamento \+ chiavi F10.  Per ulteriori informazioni, vedere [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Aggiungere una proprietà personalizzata.  La proprietà viene visualizzata nella finestra **Proprietà** quando si sceglie un progetto SharePoint in **Esplora soluzioni**.  Per ulteriori informazioni, vedere [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Per una procedura dettagliata in cui viene illustrato come creare, distribuire e testare un'estensione di progetto, vedere [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## Informazioni sulla relazione tra estensioni di progetto e istanze di progetto  
 Quando si crea un'estensione di progetto, questa viene caricata quando si apre qualsiasi tipo di progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono inclusi diversi modelli di progetto SharePoint, ad esempio definizioni di elenco, tipi di contenuto e ricevitori di eventi.  Tuttavia, esiste un solo tipo di progetto SharePoint.  I tipi di progetto visualizzati nella finestra di dialogo **Nuovo progetto** sono solo i modelli che raggruppano uno o più elementi di progetto SharePoint.  Poiché esiste un solo tipo di progetto SharePoint, le estensioni create per un determinato progetto si applicano a tutti i progetti SharePoint.  Ad esempio, non è possibile creare un'estensione applicabile soltanto a un progetto **Tipo di contenuto**.  
  
 Per accedere a una specifica istanza del progetto, gestire uno degli eventi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> del parametro *projectService* nell'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>.  Ad esempio, per determinare quando un progetto SharePoint viene aggiunto a una soluzione, gestire l'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>.  Per ulteriori informazioni, vedere [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## Vedere anche  
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  