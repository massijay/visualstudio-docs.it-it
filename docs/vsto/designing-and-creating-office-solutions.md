---
title: "Progettazione e creazione di soluzioni Office"
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
  - "sviluppo per Office in Visual Studio, creazione di soluzioni"
  - "Office (tipi di progetto in Visual Studio)"
  - "Soluzioni Office [sviluppo per Office in Visual Studio], creazione"
  - "soluzioni [sviluppo per Office in Visual Studio], creazione"
ms.assetid: 53c32c61-3d3a-4427-a5a7-f9c2c8f1de02
caps.latest.revision: 103
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 99
---
# Progettazione e creazione di soluzioni Office
  Visual Studio fornisce modelli di progetto che è possibile utilizzare per creare diversi tipi di soluzioni Office.  In questa sezione della documentazione vengono descritti i modelli di progetto e vengono fornite informazioni aggiuntive sulla creazione di progetti di Office.  Per informazioni su come implementare le personalizzazioni di interfaccia utente e codice dopo aver creato il progetto, vedere [Sviluppo di soluzioni Office](../vsto/developing-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Creazione di progetti Office  
 Prima di iniziare, è necessario stabilire i requisiti e individuare il tipo di soluzione più adatta alle proprie esigenze.  Ad esempio, se la soluzione Office deve essere eseguita ogni volta che viene usata l'applicazione, un componente aggiuntivo VSTO è più adatto per soddisfare le esigenze.  Se il codice è strettamente integrato con un unico documento, creare una personalizzazione a livello di documento.  Questi tipi di progetto sono disponibili come modelli di progetto Visual Studio.  Per ulteriori informazioni sui modelli di progetto inclusi in Visual Studio, vedere [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md).  Per altre informazioni sulla creazione di progetti Office, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)  
  
 I progetti Office presentano funzionalità ed elementi di progetto diversi da altri tipi di progetti in Visual Studio.  Ad esempio, quando si crea un progetto a livello di documento, il documento o cartella di lavoro nel progetto può essere aperto e modificato in Visual Studio.  Per altre informazioni, vedere [Progetti di Office in ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Scelta di una versione di .NET Framework  
 Dopo aver selezionato il tipo di progetto che meglio soddisfa le proprie esigenze, è possibile scegliere quale versione di .NET Framework utilizzare nel processo di sviluppo.  È possibile destinare le seguenti versioni di .NET Framework nei progetti di Office:  
  
-   [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]  
  
-   [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
-   [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
  
 Perché la soluzione funzioni è necessario che nei computer degli utenti finali sia installata la versione di .NET Framework di destinazione del progetto.  Ad esempio, se il progetto è per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], sui computer degli utenti finali deve essere installato [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  In questo esempio, la soluzione non verrà eseguita se nei computer degli utenti finali è installato solo .NET Framework 3.5.  
  
 Se si esegue la migrazione di un progetto di componente aggiuntivo VSTO destinato a .NET Framework 3.5, Visual Studio modifica il framework di destinazione del progetto impostandolo su [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva, a seconda della versione di Office installata.  
  
 Dopo la modifica del framework di destinazione, tuttavia, potrebbe essere necessario modificare parte del codice nel progetto se vengono utilizzate alcune funzionalità.  Per informazioni sulla modifica della versione di .NET Framework di destinazione, vedere [Procedura: destinare una versione di .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  Per ulteriori informazioni sulle modifiche che potrebbe essere necessario apportare al progetto, vedere [Migrazione di soluzioni Office a .NET Framework 4 o versioni successive](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Se Visual Studio modifica .NET Framework di destinazione per il progetto e si utilizza ClickOnce per distribuire la soluzione, assicurarsi di selezionare anche la versione corrispondente di .NET Framework nella finestra di dialogo **Prerequisiti**.  Questa selezione non viene modificata automaticamente quando si modifica il framework di destinazione per il progetto.  Per ulteriori informazioni, vedere [Procedura: installare i prerequisiti nei computer degli utenti finali per l'esecuzione delle soluzioni Office](http://msdn.microsoft.com/it-it/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
> [!NOTE]  
>  Non è possibile usare .NET Framework 3.5 o versioni precedenti nei progetti Office creati tramite [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  I progetti di Office create mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] richiedono funzionalità che sono state introdotte in [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
### Stabilire quando sono necessari gli assembly di interoperabilità primari di Office nei computer degli utenti finali  
 Per impostazione predefinita, non è necessario che gli assembly di interoperabilità primari di Office \(PIA\) siano installati nel computer dell'utente finale se la proprietà **Incorpora tipi di interoperabilità** di ogni riferimento all'assembly di interoperabilità primario nel progetto è impostata su **True**, ovvero il valore predefinito.  In questo scenario, le informazioni sul tipo per i tipi di assembly di interoperabilità primari utilizzati dalla soluzione vengono incorporate nell'assembly della soluzione quando si compila il progetto.  In fase di runtime, le informazioni sul tipo incorporate vengono utilizzate al posto degli assembly di interoperabilità primari per chiamare il modello a oggetti COM dell'applicazione di Office.  Per ulteriori informazioni su come i gli assembly di interoperabilità primari sono incorporati nella soluzione, vedere [Type Equivalence and Embedded Interop Types](http://msdn.microsoft.com/library/78892eba-2a58-4165-b4b1-0250ee2f41dc).  
  
 Se la proprietà **Incorpora tipi di interoperabilità** di ogni riferimento nel progetto è impostata su **False**, gli assembly di interoperabilità primari di Office devono essere installati e registrati nella cache di assembly globale in ogni computer dell'utente finale in cui viene eseguita la soluzione.  Nella maggior parte dei casi, gli assembly di interoperabilità primari vengono installati per impostazione predefinita con Office, ma è anche possibile includere l'assembly di interoperabilità primario ridistribuibile come prerequisito per la soluzione.  Per ulteriori informazioni sui prerequisiti, vedere [Prerequisiti per la distribuzione delle soluzioni Office](http://msdn.microsoft.com/it-it/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### Informazioni su Client Profile  
 .NET Framework Client Profile è un sottoinsieme della versione completa di .NET Framework.  È possibile scegliere .NET Framework Client Profile se è necessario utilizzare solo le funzionalità client di .NET Framework e si desidera fornire l'esperienza di distribuzione più veloce per la soluzione Office.  Per altre informazioni, vedere [Profilo client .NET Framework](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
 Quando si crea un progetto Office destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)],  [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] è la destinazione predefinita. Se si desidera sviluppare soluzioni per la versione completa di [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], è necessario impostare questa opzione dopo la creazione del progetto.  Per altre informazioni, vedere [Procedura: destinare una versione di .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## Creazione di soluzioni per l'edizione a 64 bit di Microsoft Office  
 Microsoft Office è disponibile nelle edizioni a 64 bit e a 32 bit.  Per creare soluzioni Office eseguibili in entrambe le edizioni, l'impostazione della destinazione della piattaforma per il progetto deve essere impostata su **Qualsiasi CPU**.  Questo è il valore predefinito per i progetti Office. Per altre informazioni, vedere [Compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
 Sono disponibili versioni a 32 e 64 bit separate di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che vengono utilizzate per le edizioni a 64 bit e a 32 bit di Microsoft Office.  Per altre informazioni, vedere [Panoramica di Visual Studio Tools per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## Assembly nelle soluzioni Office  
 Quando si crea un progetto di Office mediante gli strumenti di sviluppo per Office in Visual Studio, il codice scritto viene compilato in un assembly.  L'assembly viene in genere distribuito in un server condiviso o in una directory sul computer client.  
  
 Gli assembly nelle soluzioni Office vengono caricati da un'applicazione di Office.  Dopo che l'assembly viene caricato, il codice nell’assembly può rispondere agli eventi generati nell'applicazione \(ad esempio quando un utente fa clic su una voce di menu\).  Il codice nell’assembly può inoltre effettuare chiamate nel modello a oggetti per automatizzare ed estendere l'applicazione e può utilizzare una qualsiasi delle classi in [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Per altre informazioni, vedere [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md) e [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 Le soluzioni Office utilizzano i manifesti di distribuzione e di applicazione per identificare l'assembly.  I manifesti contengono informazioni su nome, versione e percorso dell'assembly, per cui l'applicazione può trovare, collegare ed eseguire l'assembly corretto.  Per altre informazioni, vedere [Manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 I progetti a livello di documento includono un documento oltre a un assembly.  Il documento agisce come front\-end dell'applicazione ed è il luogo in cui avviene l'interazione dell’utente.  Ogni documento può avere un solo assembly principale del progetto associato. Tuttavia, più documenti possono puntare allo stesso assembly.  
  
 Gli assembly nei progetti a livello di documento non sono incorporati nel documento, ma vengono archiviati in una posizione diversa e sono identificati dal manifesto di applicazione del documento.  
  
## Considerazioni sulla sicurezza per gli assembly  
 Perché una soluzione Office venga eseguita in un computer, gli assembly utilizzati dalla soluzione devono essere attendibili per l'esecuzione.  Per altre informazioni, vedere [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md).  
  
 Per impostazione predefinita, l'assembly della soluzione e tutti gli assembly di riferimento che si trovano nella cartella di output del progetto sono attendibili per l'esecuzione nel computer di sviluppo quando si compila il progetto.  Per altre informazioni, vedere [Compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
 Per motivi di sicurezza, è consigliabile creare progetti nel computer locale anziché svilupparli in un percorso condiviso.  Per altre informazioni, vedere [Sviluppo collaborativo di soluzioni Office](../vsto/collaborative-development-of-office-solutions.md).  
  
## Assembly a cui viene fatto riferimento  
 L'assembly può fare riferimento ad altri assembly elencati nei riferimenti del progetto.  Tuttavia, un assembly del progetto a livello di documento non può fare riferimento a un altro assembly del progetto a livello di documento.  
  
## Vedere anche  
 [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Progetti di Office in ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)   
 [Proprietà nei progetti di Office](../vsto/properties-in-office-projects.md)   
 [Esecuzione di soluzioni in versioni diverse di Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)   
 [Procedura: sviluppare applicazioni di Office mediante gli assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Procedura: definire le informazioni di configurazione per una soluzione Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)   
 [Utilizzo della funzionalità Office in Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Attività comuni nella programmazione con Office](../vsto/common-tasks-in-office-programming.md)   
 [Sviluppo di soluzioni Office](../vsto/developing-office-solutions.md)   
 [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  