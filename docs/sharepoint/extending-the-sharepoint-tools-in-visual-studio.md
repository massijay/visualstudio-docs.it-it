---
title: "Extending the SharePoint Tools in Visual Studio | Microsoft Docs"
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
  - "Visual Studio, extending tools"
  - "extensibility [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: 084cf4bf-aaba-4277-8032-448f2cb2a124
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Tools in Visual Studio
  Gli strumenti di SharePoint in Visual Studio soddisfano i requisiti di molti scenari di sviluppo di applicazioni.  Tuttavia, si possono riscontrare delle situazioni in cui non viene garantita la funzionalità richiesta dagli sviluppatori.  In questi casi, è possibile estendere gli strumenti di SharePoint per creare la funzionalità necessaria.  
  
## Come estendere gli strumenti di SharePoint  
 È possibile estendere il sistema di progetto di SharePoint e il nodo **Connessioni di SharePoint** nella finestra **Esplora server**.  
  
### Estensione del sistema di progetto SharePoint  
 Visual Studio include un set di modelli di progetto e modelli di elemento che è possibile utilizzare per creare soluzioni SharePoint.  Ad esempio sono disponibili modelli per i ricevitori di eventi, le definizioni di elenco, i flussi di lavoro e le web part.  È tuttavia anche possibile definire tipi personalizzati di elementi di progetto SharePoint per la creazione di componenti di SharePoint quali campi o azioni personalizzate.  È inoltre possibile creare estensioni per i tipi di elemento di progetto SharePoint già installati in Visual Studio, nonché creare estensioni per i progetti SharePoint.  
  
 Per ulteriori informazioni, vedere [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### Estensione del nodo Connessioni di SharePoint in Esplora server  
 In Visual Studio, è possibile utilizzare il nodo di**Connessioni di SharePoint** nella finestra di**Esplora server** per visualizzare molti dei componenti di uno o più siti di SharePoint locali in una visualizzazione struttura ad albero gerarchica. È anche possibile estendere il nodo di **Connessioni di SharePoint** nei modi seguenti:  
  
-   Aggiungendo nodi personalizzati.  Tale operazione è utile se si desidera visualizzare i componenti dei siti di SharePoint che non vengono visualizzati per impostazione predefinita.  
  
-   Estendendo i nodi esistenti.  Ad esempio, è possibile aggiungere un nuovo nodo figlio a un nodo esistente oppure aggiungere una voce di menu di scelta rapida a un nodo ed effettuare le attività quando uno sviluppatore fa clic sulla voce di menu.  
  
 Per ulteriori informazioni, vedere [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## Requisiti per il computer di sviluppo  
 Per creare estensioni per gli strumenti di SharePoint, il computer di sviluppo deve soddisfare gli stessi requisiti per la creazione di soluzioni SharePoint in Visual Studio.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 È inoltre consigliabile installare [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  Nell'SDK sono inclusi modelli di progetto e strumenti utili per estendere Visual Studio.  In particolare, nell'SDK è presente un modello di progetto che è possibile utilizzare per creare facilmente un pacchetto Visual Studio Extension \(VSIX\).  I pacchetti VSIX costituiscono il modo migliore per implementare le estensioni di Visual Studio in Visual Studio.  Tutte le estensioni degli strumenti di SharePoint devono essere distribuite tramite pacchetti VSIX.  Tutte le procedure dettagliate di questa documentazione presuppongono che sia stato installato l'[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  
  
 Per scaricare l'SDK, vedere [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=164562](http://go.microsoft.com/fwlink/?LinkId=164562) \(la pagina potrebbe essere in inglese\).  Per ulteriori informazioni sulle estensioni di Visual Studio, vedere [Sviluppo di estensioni di Visual Studio](../Topic/Developing%20Visual%20Studio%20Extensions.md).  
  
## Vedere anche  
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Reference &#40;SharePoint Tools Extensibility&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  