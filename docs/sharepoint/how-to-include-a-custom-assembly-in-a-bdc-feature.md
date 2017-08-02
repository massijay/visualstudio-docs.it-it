---
title: "Procedura: includere un assembly personalizzato in una funzionalit&#224; di integrazione applicativa dei dati"
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
  - "VS.SharePointTools.BDC.Add_Assemblies_Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiungere riferimenti"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], assembly personalizzato"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiungere riferimenti"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], assembly personalizzato"
ms.assetid: 2ddf44b9-5f51-4bca-b8bb-94c4bbd1c5f3
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Procedura: includere un assembly personalizzato in una funzionalit&#224; di integrazione applicativa dei dati
  Il progetto può fare riferimento ad assembly di altri progetti nella stessa soluzione.  È tuttavia necessario aggiungere questi assembly al file delle funzionalità del progetto tramite la finestra di dialogo **Assegna assembly a cui viene fatto riferimento agli oggetti LobSystem**.  
  
### Per includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati  
  
1.  In **Esplora soluzioni** selezionare la cartella contenente il modello di integrazione applicativa dei dati.  
  
2.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.  
  
3.  Nella finestra **Proprietà** selezionare la proprietà **Assemblies**, quindi fare clic sul pulsante con i puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](~/docs/sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")\).  
  
     Verrà visualizzata la finestra di dialogo **Assegna assembly a cui viene fatto riferimento agli oggetti LobSystem**.  
  
4.  Nell'elenco **Seleziona un assembly**, selezionare l'assembly personalizzato.  
  
    > [!NOTE]  
    >  Gli assembly vengono visualizzati nella finestra di dialogo **Assegna assembly a cui viene fatto riferimento agli oggetti LobSystem** solo se è stato aggiunto un riferimento al progetto che contiene l'assembly.  Per ulteriori informazioni, vedere [Procedura: aggiungere o rimuovere riferimenti utilizzando la finestra di dialogo Aggiungi riferimento](http://msdn.microsoft.com/it-it/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  Nel gruppo **Proprietà riferimento** aprire l'elenco a discesa visualizzato per la proprietà **Ambito LobSystem**, selezionare il sistema line\-of\-business dei metodi che utilizzano l'assembly personalizzato e quindi premere **OK**.  
  
    > [!NOTE]  
    >  Per eseguire il debug del codice nell'assembly personalizzato, è necessario aggiungere l'assembly al pacchetto della soluzione.  Per ulteriori informazioni, vedere [Procedura: Aggiungere e rimuovere assembly aggiuntivi](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## Vedere anche  
 [Procedura: utilizzare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)   
 [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  