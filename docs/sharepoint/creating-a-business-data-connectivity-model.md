---
title: "Creazione di un modello di integrazione applicativa dei dati"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], creazione di un modello"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], creazione di un modello"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], modello"
  - "sviluppo per SharePoint in Visual Studio, servizio di integrazione applicativa dei dati"
ms.assetid: 19fd12d0-a51a-4da4-98ac-918542e84507
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Creazione di un modello di integrazione applicativa dei dati
  È possibile creare un modello di integrazione applicativa dei dati o personalizzarne uno esistente tramite Visual Studio.  Ogni progetto SharePoint può contenere un solo modello.  Per ulteriori informazioni, vedere [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## Creazione di un nuovo modello  
 Per creare un nuovo modello, creare un progetto **Modello di integrazione applicativa dei dati** o aggiungere un elemento **Modello di integrazione applicativa dei dati** a un **Progetto SharePoint vuoto**.  
  
> [!NOTE]  
>  È necessario che nel computer sia installato [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)].  
  
 In Visual Studio verrà aggiunta una cartella al progetto.  Il nome di questa cartella corrisponde a quello specificato per l'elemento **Modello di integrazione applicativa dei dati** nella finestra di dialogo **Aggiungi nuovo elemento**.  Se si crea un nuovo progetto **Modello di integrazione applicativa dei dati**, in Visual Studio la cartella verrà denominata **BdcModel1**.  
  
 Alla nuova cartella verranno aggiunti automaticamente i file seguenti:  
  
|File|Descrizione|  
|----------|-----------------|  
|File di definizione del modello|Contiene l'XML che definisce le entità, i metodi, gli oggetti del sistema line of business \(LOB\) e altri metadati che descrivono il modello.<br /><br /> Modificare i metadati contenuti in questo file tramite la finestra di progettazione dell'integrazione applicativa dei dati, **Esplora integrazione applicativa dei dati**, la finestra **Dettagli metodo di integrazione applicativa dei dati** e la finestra **Proprietà**.|  
|File di codice servizio dell'entità|Contiene i metodi che consentono di recuperare, aggiornare ed eliminare istanze dell'entità predefinita.|  
  
 Per definire le proprietà di un'entità, modificare il file di codice dell'entità.  Per ulteriori informazioni, vedere [Procedura: aggiungere un'entità al modello](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Per recuperare, aggiornare ed eliminare istanze di un'entità, aggiungere codice al file di codice servizio dell'entità.  Per ulteriori informazioni, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Quando si compila il progetto, in Visual Studio viene creato un assembly.  Assicurarsi di non aggiungere al progetto altri elementi che aggiungono codice all'assembly del progetto, ad esempio un elemento **Flusso di lavoro sequenziale** o un elemento **Web part**.  Il codice per tale elemento non verrà eseguito quando si distribuisce la soluzione, in quanto il pacchetto della soluzione non copia l'assembly nella Global Assembly Cache.  Il pacchetto della soluzione distribuisce l'assembly solo al database di integrazione applicativa dei dati in SharePoint.  
  
> [!NOTE]  
>  Visual Studio copia l'assembly in entrambi i percorsi sul computer locale quando si esegue il debug del progetto.  
  
## Aggiunta di un modello esistente  
 È possibile importare un modello creato tramite altri strumenti, ad esempio SharePoint Designer.  È possibile scegliere di importare nel progetto un modello esistente nelle seguenti situazioni:  
  
-   Per personalizzare un modello già distribuito in una server farm di SharePoint.  
  
-   Per assemblare e distribuire un modello esistente a più server farm di SharePoint.  
  
 In entrambi i casi i sistemi line of business \(LOB\) definiti nel modello importato non sono interessati e continueranno a funzionare come previsto.  Per aggiungere un modello esistente a un progetto SharePoint, utilizzare la finestra di dialogo di Visual Studio **Aggiungi elemento esistente**.  Per ulteriori informazioni, vedere [Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
 È possibile aggiungere un sistema line\-of\-business \(LOB\) di tipo assembly .NET Framework al modello importato selezionando un'opzione in **Aggiungi LobSystem di assembly .NET**.  Ciò consente di scrivere codice personalizzato e utilizzare una finestra di progettazione per definire i metadati per il modello importato.  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)|Viene illustrato come creare un nuovo modello di integrazione applicativa dei dati.|  
|[Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Viene illustrato come importare un modello esistente in un progetto SharePoint.|  
|[Procedura: utilizzare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Viene descritto come fornire stringhe unite con i metadati del modello quando il modello viene utilizzato da una web part o una pagina Web.|  
|[Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Viene illustrato come includere un assembly personalizzato nella funzionalità.|  
  
  