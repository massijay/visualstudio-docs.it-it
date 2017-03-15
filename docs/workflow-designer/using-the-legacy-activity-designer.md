---
title: "Utilizzo dell&#39;ActivityDesigner legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "attività, aggiunta figlio"
  - "attività, configurazione"
  - "attività, creazione personalizzata"
  - "ActivityDesigner"
  - "attività figlio, aggiunta"
  - "attività personalizzate"
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Utilizzo dell&#39;ActivityDesigner legacy
In questo argomento viene descritto come utilizzare ActivityDesigner in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy.Utilizzare la finestra di progettazione legacy quando si fa riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o a [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 ActivityDesigner consente di creare attività personalizzate.  
  
## Creazione di un'attività personalizzata  
 Seguire questi passaggi per creare un'attività personalizzata utilizzando la Finestra di progettazione dell’attività:  
  
1.  Scegliere **Aggiungi attività** dal menu **Progetto**.  
  
2.  Selezionare l’**Attività** o il modello di **Attività \(con separazione del codice\)**.  
  
    1.  Utilizzare il modello di **Attività** per creare un'attività con definizione di attività e codice utente nello stesso file di codice.  
  
    2.  Utilizzare il modello **Attività \(con separazione del codice\)** per creare un'attività con la definizione di attività espressa con markup del flusso di lavoro e codice utente in un file di codice separato.  
  
3.  Digitare un nome di attività o mantenere il nome predefinito e quindi fare clic su **Aggiungi**.  
  
 È inoltre possibile creare un insieme di attività personalizzate creando un progetto nuovo di tipo **Workflow Activity Library**.Per ulteriori informazioni su questo tipo di progetto, vedere [Procedura: creare una libreria di attività del flusso di lavoro \(legacy\)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).  
  
## Configurazione di un'attività.  
 Mentre la Finestra di progettazione dell’attività è attiva, è possibile utilizzare il visualizzatore proprietà per configurare le proprietà elencate nella tabella seguente.  
  
|Proprietà|Commenti|  
|---------------|--------------|  
|**Name**|Nome dell’attività.|  
|**Base Class**|Classe di base dalla quale è derivata l’attività.La classe di base predefinita è [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020).Nella finestra **Proprietà**, fare clic sui puntini di sospensione **\[...\]**della **Classe di base** per selezionare un'altra classe di base in [Finestra di dialogo Cerca e seleziona un tipo .NET \(legacy\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|  
|**Description**|Descrizione dell'attività definita dall'utente.|  
|**Enabled**|Impostare su **True** per impostazione predefinita per abilitare esecuzione e convalida dell’attività.Impostare su **False** per impostazione predefinita per disabilitare esecuzione e convalida dell’attività.Per informazioni su esecuzione e convalida di attività, vedere [Sviluppo di attività del flusso di lavoro](http://go.microsoft.com/fwlink?LinkID=65024).|  
  
## Aggiunta di attività figlio.  
 È possibile trascinare le attività figlio dalla Casella degli strumenti all'attività che si sta progettando.È quindi possibile configurare ogni attività figlio utilizzando il visualizzatore proprietà.  
  
## Vedere anche  
 [Sviluppo di attività del flusso di lavoro](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Creazione di attività personalizzate](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)   
 [Esempi di attività personalizzate](http://go.microsoft.com/fwlink?LinkID=65022)   
 [Procedura: creare una libreria di attività del flusso di lavoro \(legacy\)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [Utilizzo di Progettazione flussi di lavoro legacy](../workflow-designer/using-the-legacy-workflow-designer.md)