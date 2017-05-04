---
title: "Linee guida per l&#39;importazione di flussi di lavoro riutilizzabili | Microsoft Docs"
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
  - "importazione di elementi [sviluppo per SharePoint in Visual Studio]"
  - "flussi di lavoro riutilizzabili [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, importazione di elementi"
  - "sviluppo per SharePoint in Visual Studio, flussi di lavoro riutilizzabili"
ms.assetid: 851043dd-ecbe-49ab-b5b7-5ea7b699df12
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Linee guida per l&#39;importazione di flussi di lavoro riutilizzabili
  Per importare flussi di lavoro riutilizzabili creati in SharePoint Designer, utilizzare il modello di progetto Importa flusso di lavoro riutilizzabile SharePoint 2010 in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Questo modello importa un *flusso di lavoro* *dichiarativo* \(solo [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\) e lo converte in un *flusso di lavoro di codice*, ovvero in un flusso di lavoro migliorabile tramite codice [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] o [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)].  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Procedura dettagliata: Importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 Tuttavia, il modello Importa flusso di lavoro riutilizzabile SharePoint 2010 può importare solo soluzioni di tipo farm.  Se si desidera distribuire il flusso di lavoro come soluzione creata mediante sandbox, bisogna importalo come modello Importa pacchetto di soluzione SharePoint 2010.  Tuttavia, in questo caso, non è possibile convertirlo in un flusso di lavoro di codice e quindi non sarà possibile modificarlo.  
  
## Importazione di flussi di lavoro riutilizzabili tramite il modello Importa flusso di lavoro riutilizzabile  
 Se si importa un flusso di lavoro riutilizzabile utilizzando il modello Importa flusso di lavoro riutilizzabile SharePoint 2010, sarà possibile eseguire o modificare la soluzione proprio come con qualsiasi altra soluzione SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], tuttavia potrebbe essere necessario correggere manualmente alcuni elementi.  
  
### Importazione di form di attività  
 Il modello di progetto Importa flusso di lavoro riutilizzabile SharePoint 2010 importa tutti i form di associazione e inizializzazione, ma importa un solo form di attività poiché lo schema di codice del flusso di lavoro consente la presenza di un solo form di attività.  Qualsiasi form di attività aggiuntivo dalla soluzione del flusso di lavoro originale viene inserito nella cartella **Altri file importati** in **Esplora soluzioni**.  
  
## Importazione di flussi di lavoro riutilizzabili tramite il modello Importa pacchetto di soluzione SharePoint 2010  
 Se si importa un flusso di lavoro riutilizzabile utilizzando il modello Importa pacchetto di soluzione SharePoint 2010, è necessario considerare i seguenti problemi:  
  
-   Dopo avere importato il flusso di lavoro, è possibile distribuirlo ed eseguirlo immediatamente [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] premendo F5.  Tuttavia, se si modifica un qualsiasi elemento del flusso di lavoro nella soluzione importata, potrebbe essere necessario correggere manualmente gli elementi nel progetto prima di poter distribuire ed eseguire il flusso di lavoro.  
  
-   Poiché il flusso di lavoro è dichiarativo, non è possibile aggiungervi codice.  Per convertire il flusso di lavoro in un flusso di lavoro di codice, è necessario importarlo in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tramite il modello Importa flusso di lavoro riutilizzabile SharePoint 2010.  
  
-   Sebbene sia possibile modificare il file di Progettazione flussi di lavoro \(con estensione xoml\) in visualizzazione Progettazione, è consigliabile modificarlo in visualizzazione Origine, poiché Progettazione flussi di lavoro visualizza falsi errori.  
  
-   L'esecuzione del debug nel flusso di lavoro non funziona per il contenuto dichiarativo.  I punti di interruzione impostati in [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] non vengono rilevati.  
  
## Importazione di soluzioni di flussi di lavoro riutilizzabili globalmente  
 Non è possibile importare flussi di lavoro riutilizzabili globalmente utilizzando il modello Importa flusso di lavoro riutilizzabile SharePoint 2010.  Per importare un flusso di lavoro riutilizzabile globalmente, è necessario convertirlo in un flusso di lavoro riutilizzabile non globalmente o utilizzare il modello Importa pacchetto di soluzione SharePoint 2010.  
  
 Per convertirlo, fare una copia del flusso di lavoro riutilizzabile globalmente in SharePoint Designer \(aprendo il menu di scelta rapida per il flusso di lavoro e selezionando **Salva come copia**\).  Quindi importare il nuovo flusso di lavoro riutilizzabile con il modello Importa flusso di lavoro riutilizzabile SharePoint 2010 in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Per importare il flusso di lavoro riutilizzabile globalmente senza modificarlo, utilizzare il modello Importa pacchetto di soluzione SharePoint 2010.  Se si utilizza questo metodo, il flusso di lavoro non verrà convertito in un flusso di lavoro di codice e rimarrà un flusso di lavoro dichiarativo.  
  
## Vedere anche  
 [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Procedura dettagliata: Importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  