---
title: "Procedura: aggiungere un file di risorse"
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
  - "file di risorse [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, file di risorse"
ms.assetid: 2b4ac232-992e-4070-8e98-6f11eb88e1a8
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Procedura: aggiungere un file di risorse
  I comandi per l'aggiunta di file di risorse sono disponibili nel menu di scelta rapida del nodo della soluzione e dei nodi della funzionalità in Esplora soluzioni.  Per ulteriori informazioni, vedere [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
### Per aggiungere un file di risorse globale a una soluzione SharePoint  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aprire una soluzione SharePoint.  
  
2.  In **Esplora soluzioni** scegliere il nodo del progetto SharePoint, quindi, nella barra dei menu scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
3.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare il nodo **File di risorse globali**, quindi scegliere il pulsante **Aggiungi**.  
  
    > [!NOTE]  
    >  Il modello di elemento del progetto File di risorse globali viene visualizzato solo quando viene selezionato un elemento di progetto SharePoint.  
  
4.  Nella finestra di dialogo **Aggiungi risorsa** selezionare un'impostazione cultura per il file di risorse, ad esempio inglese \(Stati Uniti\).  
  
     Questa operazione aggiunge un file di risorse globale alla soluzione nel formato Resource*x*.**.***culture.***.**resx, ad esempio Resource1.en\-US.resx.  
  
5.  Quando **Editor di risorse** viene aperto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aggiungere le risorse al file di risorse.  
  
### Per aggiungere un file di risorse funzionalità a una funzionalità SharePoint  
  
1.  Se la soluzione SharePoint non è già aperta in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aprire la soluzione.  
  
2.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il nome di una funzionalità nel nodo **Funzionalità** quindi scegliere **Aggiungi risorsa funzionalità**.  
  
     Questo passaggio aggiunge un file di risorse alla funzionalità in formato *ResourceFileName***.***culture***.**resx, ad esempio, Feature1.en\-US.resx.  
  
3.  Quando **Editor di risorse** viene aperto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aggiungere le risorse al file di risorse.  
  
## Vedere anche  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  