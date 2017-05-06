---
title: "Procedura: modificare una configurazione di distribuzione SharePoint"
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
  - "VS.SharePointTools.Project.DeploymentConfig"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, distribuzione"
ms.assetid: bff1895b-d3fe-4ec0-ba91-f8884dc35957
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Procedura: modificare una configurazione di distribuzione SharePoint
  È possibile creare una configurazione di distribuzione o modificarne una esistente.  Ad esempio è possibile eseguire un solo passaggio o modificare l'ordine dei passaggi del processo di distribuzione.  Potrebbe essere necessario creare o modificare le configurazioni di distribuzione poiché le configurazioni incorporate e aggiunte a livello di codice non possono essere modificate.  
  
## Creazione di una configurazione di distribuzione SharePoint  
  
#### Per creare una configurazione di distribuzione SharePoint  
  
1.  In **Esplora soluzioni**, scegliere un progetto SharePoint, quindi sulla barra dei menu scegliere **Progetto** *ProjectName* **Proprietà**.  
  
2.  Nella scheda **SharePoint**, scegliere il pulsante **Nuovo**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuova configurazione distribuzione**.  
  
3.  Nella casella di testo **Nome** inserire un nome per la configurazione di distribuzione.  
  
4.  Nel riquadro **Passaggi di distribuzione disponibili**, selezionare i passaggi che si desiderano aggiungere alla configurazione di distribuzione, scegliendo il \(**\>**\) pulsante e quindi selezionando il pulsante **OK**.  
  
    > [!NOTE]  
    >  Se è stato configurato un comando di pre o post\-distribuzione, questi passaggi vengono eseguiti solamente se aggiunti ad una configurazione di distribuzione personalizzata.  
  
## Modifica della configurazione di distribuzione attiva  
  
#### Per modificare la configurazione di distribuzione attiva  
  
1.  In **Esplora soluzioni**, scegliere un progetto SharePoint, quindi sulla barra dei menu scegliere **Progetto** *ProjectName* **Proprietà**.  
  
2.  Scegliere la scheda **SharePoint**.  
  
3.  Nella casella di riepilogo **Configurazione distribuzione attiva**, scegliere il nome della configurazione di distribuzione che si desidera utilizzare.  
  
## Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  