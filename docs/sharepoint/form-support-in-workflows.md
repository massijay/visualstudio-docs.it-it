---
title: "Supporto dei form nei flussi di lavoro | Microsoft Docs"
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
  - "sviluppo per SharePoint in Visual Studio, flussi di lavoro"
  - "flussi di lavoro [sviluppo per SharePoint in Visual Studio]"
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Supporto dei form nei flussi di lavoro
  In un flusso di lavoro possono essere utilizzati quattro tipi di form, ovvero di associazione, di avvio, di attività e di modifica.  Questi tipi di form possono essere basati su un form ASPX o InfoPath.  Il livello di supporto fornito da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per un particolare form dipende da diversi fattori descritti nelle tabelle riportate di seguito.  Per ulteriori informazioni sui tipi di form del flusso di lavoro, vedere [Cenni preliminari sui form del flusso di lavoro](http://go.microsoft.com/fwlink/?LinkId=185228) sul sito Web MSDN.  
  
## Refactoring XML  
 Quando si aggiunge un form di associazione o di avvio ASPX a un elemento del progetto flusso di lavoro [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], tramite [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene effettuato automaticamente il refactoring di XML nel file Elements.xml del flusso di lavoro per mantenere sincronizzato l'attributo che fa riferimento al form di associazione o di avvio, ogni volta che il nome del form o il percorso di distribuzione viene aggiornato o il form viene eliminato.  Tuttavia, quando si utilizzano altri tipi di form in un flusso di lavoro, ad esempio un form di attività o di modifica, il refactoring del file Elements.xml non viene effettuato.  
  
## Supporto di form nei nuovi flussi di lavoro Visual Studio  
 Nella tabella seguente viene elencato il supporto di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per i diversi tipi di form in ASPX o InfoPath nei flussi di lavoro creati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo di form|Flusso di lavoro creato in Visual Studio con un form ASPX|Flusso di lavoro creato in Visual Studio utilizzando un form InfoPath|  
|------------------|---------------------------------------------------------------|---------------------------------------------------------------------------|  
|Associazione|-   Un form di associazione ASPX può essere aggiunto al flusso di lavoro tramite il modello di elemento **Form di associazione flusso di lavoro**.<br />-   Quando il form viene aggiunto, rinominato o eliminato oppure quando il relativo percorso di distribuzione viene modificato, viene effettuato il refactoring del file Elements.xml del flusso di lavoro.<br />-   Per ulteriori informazioni, vedere [Procedura dettagliata: creazione di un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-   Non è disponibile alcun modello di form di associazione InfoPath in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   Non esiste alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />-   Il refactoring del file Elements.xml del flusso di lavoro non viene effettuato.|  
|Avvio|-   Un form di avvio ASPX può essere aggiunto al flusso di lavoro tramite il modello di elemento **Form di avvio del flusso di lavoro**.<br />-   Quando il form viene aggiunto, rinominato o eliminato oppure quando il relativo percorso di distribuzione viene modificato, viene effettuato il refactoring del file Elements.xml del flusso di lavoro.<br />-   Per ulteriori informazioni, vedere [Procedura dettagliata: creazione di un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-   Non è disponibile alcun modello di form di associazione InfoPath in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   Non esiste alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />-   Il refactoring del file Elements.xml del flusso di lavoro non viene effettuato.|  
|Attività|-   Non è disponibile alcun modello di form di attività ASPX in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  È necessario creare una pagina applicazione a cui aggiungere codice.<br />-   Il refactoring del file Elements.xml del flusso di lavoro non viene effettuato.<br />-   Per ulteriori informazioni, vedere [Form di attività del flusso di lavoro \(SharePoint Foundation\)](http://go.microsoft.com/fwlink/?LinkId=187674)|-   Non è disponibile alcun modello di form di attività InfoPath in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   Non esiste alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />-   Il refactoring del file Elements.xml del flusso di lavoro non viene effettuato.|  
|Modifica|-   Non è disponibile alcun modello di form di modifica ASPX in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Per aggiungere un form di modifica, è necessario creare una pagina applicazione a cui aggiungere codice.<br />-   Il refactoring del file Elements.xml del flusso di lavoro non viene effettuato.  È necessario modificarlo manualmente in base alle proprie esigenze.<br />-   Per ulteriori informazioni, vedere [Form di modifica del flusso di lavoro \(SharePoint Foundation\)](http://go.microsoft.com/fwlink/?LinkId=187675)|-   Non è disponibile alcun modello di form di modifica InfoPath in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   Non esiste alcuna integrazione tra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e InfoPath Designer.<br />-   Il refactoring del file Elements.xml del flusso di lavoro non viene effettuato.|  
  
## Supporto di form nei flussi di lavoro riutilizzabili SharePoint importati  
 Nella tabella seguente viene elencato il supporto di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per i diversi tipi di form in ASPX o InfoPath nei flussi di lavoro riutilizzabili SharePoint importati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Tipo di form|Flusso di lavoro riutilizzabile con form ASPX importato da SharePoint Designer|Flusso di lavoro riutilizzabile con form InfoPath importato da SharePoint Designer|  
|------------------|------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|Associazione|-   Al form viene fatto riferimento nel file Elements.xml del flusso di lavoro.<br />-   Quando il form viene rinominato o eliminato oppure quando il relativo percorso di distribuzione viene modificato, viene effettuato il refactoring del file Elements.xml del flusso di lavoro.|-   Il form viene importato ma ad esso non viene fatto riferimento nel file Elements.xml del flusso di lavoro.<br />-   Il refactoring del file Elements.xml del flusso di lavoro non viene effettuato.|  
|Avvio|-   Il form a cui viene fatto riferimento nel flusso di lavoro nel file Elements.xml del flusso di lavoro.<br />-   Quando il form viene rinominato o eliminato oppure quando il relativo percorso di distribuzione viene modificato, viene effettuato il refactoring del file Elements.xml del flusso di lavoro.|-   Il form viene importato ma ad esso non viene fatto riferimento nel file Elements.xml del flusso di lavoro.<br />-   Il refactoring del file Elements.xml del flusso di lavoro non viene effettuato. **Note:**  Affinché questo scenario sia valido, è necessario aggiungere e modificare regole e proprietà.|  
|Attività|-   Al form viene fatto riferimento nel file Elements.xml del flusso di lavoro.<br />-   Il refactoring del file Elements.xml del flusso di lavoro non viene effettuato.|-   Il form viene importato ma ad esso non viene fatto riferimento nel file Elements.xml del flusso di lavoro.<br />-   Il refactoring del file Elements.xml del flusso di lavoro non viene effettuato. **Note:**  Affinché questo scenario sia valido, è necessario aggiungere e modificare regole e proprietà.|  
|Modifica|Non applicabile.  Impossibile creare form di modifica ASPX in SharePoint Designer.|Non applicabile.  Impossibile creare form di modifica InfoPath in SharePoint Designer, a eccezione del flusso di lavoro SharePoint Server incorporato, non incluso nel file con estensione wsp quando il flusso di lavoro viene esportato.|  
  
## Vedere anche  
 [Procedura dettagliata: creazione di un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  