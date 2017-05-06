---
title: "Dati memorizzati nella cache nelle personalizzazioni a livello di documento"
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
  - "memorizzazione di dati nella cache [sviluppo per Office in Visual Studio], informazioni sulla memorizzazione di dati nella cache"
  - "dati [sviluppo per Office in Visual Studio], cache"
  - "dati [sviluppo per Office in Visual Studio], soluzioni a livello di documento"
  - "memorizzazione di dati nella cache [sviluppo per Office in Visual Studio], informazioni sulla memorizzazione di dati nella cache"
  - "isole di dati [sviluppo per Office in Visual Studio]"
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio], modello dati"
  - "visualizzazione [sviluppo per Office in Visual Studio]"
ms.assetid: 84808462-2c5d-4dc8-ab69-491d492b4a51
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Dati memorizzati nella cache nelle personalizzazioni a livello di documento
  Uno degli obiettivi principali delle personalizzazioni a livello di documento consiste nel separare i dati dalla visualizzazione nei documenti di Office.  Per dati si intendono le informazioni memorizzate nel documento, ad esempio numeri e testo.  Per visualizzazione si intende l'interfaccia utente e il modello a oggetti di Microsoft Office Word e Microsoft Office Excel.  
  
 Visual Studio separa i dati dalla visualizzazione nelle personalizzazioni a livello di documento consentendo di incorporare i dati come un'*isola di dati*, anche definita *cache dei dati*.  Tale funzionalità consente di leggere o modificare i dati direttamente senza avviare Word o Excel.  Ciò risulta utile quando è necessario modificare i dati di documenti contenuti in un server in cui non è stato installato Microsoft Office.  Word ed Excel sono destinati all'utilizzo in ambienti client; non sono progettati per essere eseguiti in un server.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Per ulteriori informazioni sulle personalizzazioni a livello di documento, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) e [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
## Informazioni sul modello di programmazione dei dati memorizzati nella cache  
 L'isola di dati può contenere qualsiasi oggetto della soluzione, purché soddisfi determinati requisiti.  Alcuni esempi di oggetti che è possibile includere in un'isola di dati sono gli oggetti <xref:System.Data.DataSet>, gli oggetti <xref:System.Data.DataTable> e qualsiasi altro oggetto serializzabile mediante la classe <xref:System.Xml.Serialization.XmlSerializer>.  Per ulteriori informazioni, vedere [Memorizzazione di dati nella cache](../vsto/caching-data.md).  
  
 Per fornire la visualizzazione dei dati memorizzati nella cache è possibile associare controlli Windows Form e *controlli host* contenuti nel documento a oggetti contenuti nell'isola di dati.  Questa associazione dati consente di garantire la sincronizzazione tra l'isola di dati e i controlli associati ai dati.  È inoltre possibile aggiungere ai dati codice di convalida indipendente dai controlli.  Per ulteriori informazioni, vedere [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 I controlli host sono versioni estese di oggetti nativi appartenenti ai modelli a oggetti di Excel e Word.  A differenza degli oggetti nativi, i controlli host possono essere associati direttamente agli oggetti dati gestiti.  Per ulteriori informazioni, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md) e [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## Accesso ai dati memorizzati nella cache sul server  
 Per accedere ai dati di un documento memorizzati nella cache è possibile utilizzare la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>.  Questa classe appartiene al [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e può essere utilizzata in un server senza eseguire Excel o Word.  Quando un utente apre un documento i cui dati memorizzati nella cache sono stati modificati, tutti i controlli associati ai dati vengono sincronizzati automaticamente con la cache. Pertanto, l'utente sarà in grado di accedere a una versione aggiornata del documento.  Per ulteriori informazioni, vedere [Accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel e Word non vengono utilizzati per scrivere nei dati sul server, ma solo per visualizzarli sul client.  Queste due applicazioni possono anche non essere installate sul server.  Ciò consente di migliorare la scalabilità nonché di velocizzare l'elaborazione batch dei documenti che contengono isole di dati.  
  
## Memorizzazione di dati nella cache per l'utilizzo offline  
 La memorizzazione dei dati nell'isola di dati offre la possibilità di accedere a scenari offline.  Quando un utente apre per la prima volta un documento o lo richiede al server, l'isola di dati contiene i dati più recenti.  L'isola di dati viene memorizzata nella cache del documento ed è quindi disponibile per l'utilizzo offline.  I dati possono essere modificati dall'utente o tramite codice, anche senza una connessione attiva.  Alla riconnessione successiva, le modifiche apportate ai dati possono essere propagate a un'origine dati su server.  
  
## Confronto fra dati memorizzati nella cache e web part XML personalizzate  
 Le web part XML personalizzate sono state introdotte in Microsoft Office System 2007 per consentire la memorizzazione di elementi XML arbitrari in un documento.  Benché gli scenari in cui le web part XML personalizzate risultano utili corrispondano agli scenari in cui conviene utilizzare una cache dei dati, esistono alcune differenze tra l'isola di dati e le web part XML personalizzate.  Per ulteriori informazioni sulle web part XML personalizzate, vedere [Cenni preliminari sulle web part XML personalizzate](../vsto/custom-xml-parts-overview.md).  
  
 Nella tabella seguente sono elencati alcuni punti in comune nonché alcune differenze fra l'isola di dati e le web part XML personalizzate.  
  
||Cache di dati|Web part XML personalizzate|  
|-|-------------------|---------------------------------|  
|Applicazioni di Office in grado di utilizzare la cache di dati o le web part XML personalizzate|Personalizzazioni a livello di documento per le applicazioni seguenti:<br /><br /> -   Excel<br />-   Word|Soluzioni a livello di documento e soluzioni a livello di applicazione per le applicazioni seguenti:<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|  
|Tipi di dati memorizzabili|Qualsiasi oggetto pubblico contenuto nell'assembly di personalizzazione che soddisfi determinati requisiti.  Per ulteriori informazioni, vedere [Memorizzazione di dati nella cache](../vsto/caching-data.md).|Qualsiasi tipo di dati XML.|  
|Accesso ai dati senza avviare le applicazioni di Microsoft Office|Mediante la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> fornita dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Mediante le classi nello spazio dei nomi <xref:System.IO.Packaging> o tramite l'SDK del formato Open XML.|  
  
## Vedere anche  
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  