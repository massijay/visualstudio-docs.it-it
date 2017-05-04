---
title: "Procedura: installare il runtime ridistribuibile di Microsoft Visual Studio Tools per Office | Microsoft Docs"
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
  - "strumenti di sviluppo per Office in Visual Studio (installazione)"
  - "runtime Office [sviluppo per Office in Visual Studio]"
ms.assetid: ac7a9ad3-e810-4d7f-a0e2-9992c9036b8d
caps.latest.revision: 94
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 93
---
# Procedura: installare il runtime ridistribuibile di Microsoft Visual Studio Tools per Office
  Visual Studio 2010 Tools per Office Runtime deve essere installato su tutti i computer che eseguono le soluzioni create tramite gli strumenti di sviluppo di Microsoft Office in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Il runtime viene installato automaticamente all'installazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e di Microsoft Office.  Per ulteriori informazioni, vedere [Scenari di installazione del runtime di Visual Studio Tools per Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 Attenersi alle seguenti istruzioni di installazione manuale, se si verificano le situazioni riportate di seguito:  
  
-   È necessario installare il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] su un server.  Ad esempio, si desidera utilizzare la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per gestire soluzioni a livello di documento su un server.  
  
-   È necessario installare il runtime in un computer su cui sono già installati tutti i prerequisiti delle soluzioni di Office.  
  
    > [!NOTE]  
    >  Per installare .NET Framework e [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], è necessario essere un amministratore del computer di sviluppo.  
  
### Per installare l'assembly nel runtime di Visual Studio Tools per Office  
  
1.  Installare [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versione successiva.  
  
    -   Per scaricare [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], vedere [Microsoft .NET Framework 4 \(programma di installazione Web\)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Per scaricare [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], vedere [Microsoft .NET Framework 4 Client Profile \(programma di installazione Web\)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Per scaricare [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], vedere [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Per installare [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], eseguire il file vstor\_redist.exe.  
  
     È possibile scaricare questi file di installazione da [Visual Studio 2010 Tools per Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384).  I prerequisiti per [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] corrispondono a quelli per .NET Framework.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] include i Language Pack.  Se l'installazione di Windows è impostata su una lingua diversa dall'inglese, è possibile visualizzare i messaggi di runtime nella stessa lingua utilizzata da Windows.  Analogamente, se gli utenti finali installano [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ed eseguono le soluzioni in versioni di Windows impostate su una lingua diversa dall'inglese, verranno visualizzati i messaggi di runtime nella stessa lingua di Windows.  In alcuni casi, potrebbe essere necessario installare Language Pack aggiuntivi.  Ad esempio, potrebbero essere necessari Language Pack aggiuntivi se la copia di Windows utilizza più di una impostazione di lingua oppure se l'utente passa a un'altra lingua dopo aver già stato installato [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  È possibile trovare i Language Pack in [Language Pack di Microsoft Visual Studio 2010 Tools per Microsoft Office System \(versione runtime 4.0 Runtime\)](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## Vedere anche  
 [Guida introduttiva &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Configurazione di un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Procedura: configurare un computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Procedura: installare assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Gestione dei documenti di un server utilizzando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  