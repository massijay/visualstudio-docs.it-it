---
title: "Procedura: aggiungere un nuovo elemento ad un progetto flusso di lavoro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Procedura: aggiungere un nuovo elemento ad un progetto flusso di lavoro
Dopo aver creato un progetto flusso di lavoro, è possibile aggiungervi attività del flusso di lavoro, finestre di progettazione e altri elementi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comuni.  
  
 Nella tabella seguente sono elencati gli elementi [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che è possibile aggiungere a un progetto flusso di lavoro.  
  
|Nome|Descrizione|  
|----------|-----------------|  
|Attività|Attività che deve essere composta da altre attività.Selezionando questo elemento viene aggiunto al progetto lo stesso file XAML ottenuto quando si seleziona il modello **Attività libreria** per un nuovo progetto.[!INCLUDE[crabout](../test/includes/crabout_md.md)] questa procedura, vedere [Procedura: creare una libreria attività](../workflow-designer/how-to-create-an-activity-library.md).|  
|ActivityDesigner|Finestra di progettazione per personalizzare l'esperienza di progettazione di un'attività.Selezionando questo elemento vengono aggiunti al progetto gli stessi file ottenuti quando si seleziona il modello **Libreria ActivityDesigner** per un nuovo progetto.[!INCLUDE[crabout](../test/includes/crabout_md.md)] questa procedura, vedere [Procedura: creare una libreria ActivityDesigner](../workflow-designer/how-to-create-an-activity-designer-library.md).|  
|Attività codice|Attività con la logica di esecuzione scritta nel codice.Un file di codice sorgente con un override del metodo <xref:System.Activities.CodeActivity.Execute%2A> è già generato automaticamente.|  
|Servizio flusso di lavoro WCF|Servizio [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] compilato utilizzando le attività del flusso di lavoro.Selezionando questo elemento vengono aggiunti al progetto gli stessi file ottenuti quando si seleziona il modello **Applicazione di servizi flusso di lavoro WCF** per un nuovo progetto.[!INCLUDE[crabout](../test/includes/crabout_md.md)] questa procedura, vedere [Procedura: creare un'applicazione del servizio flusso di lavoro WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|  
  
### Per aggiungere un nuovo elemento a un progetto flusso di lavoro  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
     Verrà aperta la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Nel riquadro **Modelli installati** selezionare il gruppo **Flusso di lavoro**.  
  
3.  Selezionare uno dei quattro elementi.Nella tabella precedente sono elencate le selezioni disponibili.  
  
4.  Digitare un nome appropriato per l'elemento nella casella **Nome** nella parte inferiore della finestra di dialogo.  
  
5.  Fare clic su **Aggiungi** per aggiungere l'elemento al progetto flusso di lavoro corrente.  
  
## Vedere anche  
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)