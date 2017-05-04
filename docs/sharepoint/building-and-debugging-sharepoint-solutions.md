---
title: "Compilazione e debug delle soluzioni SharePoint | Microsoft Docs"
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
  - "sviluppo per SharePoint in Visual Studio, compilazione e debug"
  - "sviluppo per SharePoint in Visual Studio, debug"
ms.assetid: c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Compilazione e debug delle soluzioni SharePoint
  I processi di compilazione e debug delle soluzioni SharePoint in genere sono analoghi a quelli eseguiti per altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Negli argomenti di questa sezione vengono illustrate le differenze esistenti.  
  
## Output di progetto per le soluzioni SharePoint  
 La compilazione di soluzioni SharePoint comporta la creazione di assembly e di un file del pacchetto della soluzione \(con estensione wsp\).  Nella tabella che segue sono indicati i percorsi di tali file durante una compilazione.  
  
|Elemento di compilazione|Cartella di output|  
|------------------------------|------------------------|  
|Assembly, database di programma e file wsp.|*ProjectName*\\bin\\debug o *ProjectName*\\bin\\release|  
|File degli elementi di progetto SharePoint.|*ProjectName*\\pkg\\debug o *ProjectName*\\pkg\\release|  
|File intermedi di compilazione.|*ProjectName*\\obj\\debug o *ProjectName*\\obj\\release|  
|File intermedi di pacchetto.|*ProjectName*\\pkgobj\\debug o *ProjectName*\\pkgobj\\release|  
  
## Compilazione di soluzioni SharePoint  
 Per compilare soluzioni SharePoint, nel computer di sviluppo deve essere installata la versione corretta del server SharePoint.  In caso contrario, la compilazione delle soluzioni SharePoint corrisponderà alla compilazione di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Per ulteriori informazioni, vedere [Procedura: compilare soluzioni SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## Debug e test delle soluzioni SharePoint  
 Prima di eseguire il debug, in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene eseguita la copia del pacchetto wsp nel server SharePoint, vengono attivati il sito e le funzionalità con ambito Web e, in alcuni casi, viene avviato il progetto.  In altri casi, potrebbe essere necessario aprire manualmente il progetto.  Per ulteriori informazioni, vedere [Risoluzione dei problemi relativi alle soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) e [Debug di soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## Verifica e debug delle soluzioni SharePoint utilizzando la funzionalità ALM  
 Le funzionalità di ALM di Visual Studio funzionano come di unit test e IntelliTrace e consentono di individuare con maggiore precisione i problemi delle soluzioni SharePoint.  La profilatura consente di individuare e identificare aree problematiche delle prestazioni in soluzioni SharePoint.  Per ulteriori informazioni, vedere [Verifica e debug del codice di SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) e [Profilatura delle prestazioni di applicazioni di SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## Sicurezza durante il processo di compilazione  
 Per la creazione di pacchetti o la distribuzione di soluzioni SharePoint, è necessario disporre in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] delle autorizzazioni per la copia dei file nel server SharePoint.  È inoltre necessario eseguire [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come processo con privilegi elevati e l'account utente deve essere quello di Amministratore raccolta siti sul server SharePoint.  È infine necessario specificare se il progetto è una soluzione creata mediante sandbox o una soluzione farm.  Per ulteriori informazioni, vedere [Differenze tra soluzioni create mediante sandbox e soluzioni farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## Utilizzo del comando Pulisci  
 Quando si installa una soluzione SharePoint in un server SharePoint per l'esecuzione del debug, il comando **Pulisci** non consente di disinstallare la soluzione.  Per farlo, è necessario disattivare le funzionalità tramite la configurazione di SharePoint.  
  
## Vedere anche  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Esplorazione di connessioni di SharePoint tramite Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  