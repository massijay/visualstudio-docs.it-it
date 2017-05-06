---
title: "Gestione dei documenti di un server utilizzando la classe ServerDocument"
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
  - "documenti [sviluppo per Office in Visual Studio], gestione su server"
  - "documenti Office [sviluppo per Office in Visual Studio], gestione su server"
  - "ServerDocument (classe), gestione di documenti su server"
ms.assetid: 1ac90e89-d07d-4874-9d24-6741d6679a21
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Gestione dei documenti di un server utilizzando la classe ServerDocument
  È possibile utilizzare la classe ServerDocument in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] per gestire molti aspetti della personalizzazione a livello di documento, anche se Microsoft Office Word e Microsoft Office Excel non sono installati.  È possibile svolgere le attività indicate di seguito.  
  
-   Accedere e modificare i dati nella cache di dati di un documento o di una cartella di lavoro.  Per ulteriori informazioni, vedere [Utilizzo dei dati memorizzati nella cache in un documento](#CachedData).  
  
-   Gestire l'assembly di personalizzazione associato a un documento.  Per ulteriori informazioni, vedere [Gestione della personalizzazione del documento](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Informazioni sulla classe ServerDocument  
 La classe ServerDocument è progettata per i computer in cui Office non è installato.  Pertanto, in genere si utilizza questa classe nelle applicazioni che non si integrano con Office, ad esempio progetti Console o Windows Form, anziché progetti Office.  Utilizzare la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> nell'assembly Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
 La classe ServerDocument per essere utilizzate nelle personalizzazioni a livello di documento create utilizzando [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Per ulteriori informazioni sugli strumenti di Visual Studio 2010 per Office runtime e sulle estensioni di Office per .NET Framework, vedere [Panoramica di Visual Studio Tools per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Se si dispone di un'applicazione legacy che utilizza la classe ServerDocument in Visual Studio Tools per Office System 3.0 Runtime \(versione runtime 3,0\), Visual Studio Tools per Office System 3.0 Runtime \(versione runtime 3,0\) deve essere installato nei computer che eseguono l'applicazione.  Visual Studio 2010 tools per Office runtime non possono eseguire queste applicazioni.  
  
##  <a name="CachedData"></a> Utilizzo dei dati memorizzati nella cache in un documento  
 La classe ServerDocument fornisce membri che si possono utilizzare con la cache di dati nei documenti personalizzati.  Per ulteriori informazioni sui dati memorizzati nella cache, vedere [Memorizzazione di dati nella cache](../vsto/caching-data.md) e [Accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Nella tabella seguente sono elencati i membri che si possono utilizzare con i dati memorizzati nella cache.  
  
|Task|Membro da utilizzare|  
|----------|--------------------------|  
|Per determinare se un documento ha una cache di dati.|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>.|  
|Per accedere ai dati memorizzati nella cache in un documento.<br /><br /> Per ulteriori informazioni, vedere [Accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).|Proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|  
  
##  <a name="CustomizationInfo"></a> Gestione della personalizzazione del documento  
 È possibile utilizzare i membri della classe ServerDocument per gestire l'assembly di personalizzazione associato a un documento.  Ad esempio, è possibile rimuovere a livello di codice la personalizzazione da un documento, in modo che il documento non sia più incluso in una personalizzazione.  
  
 Nella tabella seguente sono elencati i membri che si possono utilizzare per gestire l'assembly di personalizzazione.  
  
|Task|Membro da utilizzare|  
|----------|--------------------------|  
|Per determinare se un documento fa parte di una personalizzazione a livello di documento.|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>.|  
|Per connettere a livello di codice una personalizzazione a un documento in fase di esecuzione.<br /><br /> Per ulteriori informazioni, vedere [Procedura: associare estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md).|Uno dei metodi <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.|  
|Per rimuovere a livello di codice una personalizzazione da un documento in fase di esecuzione.<br /><br /> Per ulteriori informazioni, vedere [Procedura: rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>.|  
|Per ottenere l'URL del manifesto di distribuzione associato al documento.|Proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|  
  
## Vedere anche  
 [Procedura: associare estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Procedura: rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Panoramica di Visual Studio Tools per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Memorizzazione di dati nella cache](../vsto/caching-data.md)  
  
  