---
title: "Funzionalit&#224; fondamentali del servizio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servizi, essentials"
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzionalit&#224; fondamentali del servizio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un servizio è un contratto tra due VSPackage. Un VSPackage fornisce un set specifico di interfacce per un altro VSPackage da utilizzare.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è un insieme di package VS che fornisce servizi per altri package VS.  
  
 Ad esempio, è possibile utilizzare il servizio SVsActivityLog per ottenere un'interfaccia IVsActivityLog, che è possibile utilizzare per scrivere nel registro attività. Per altre informazioni, vedere [Procedura: utilizzare il registro attività](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce inoltre alcuni servizi predefiniti che non sono registrati. Package VS può sostituire incorporati o altri servizi, fornendo una servizio di sostituzione. Sostituzione di un solo servizio è consentito per qualsiasi servizio.  
  
 Servizi non dispongono di alcun rilevamento. È necessario conoscere l'ID di servizio \(SID\) di un servizio che si desidera utilizzare, pertanto è necessario conoscere quali interfacce fornisce. La documentazione di riferimento per il servizio fornisce queste informazioni.  
  
-   Package VS che forniscono servizi vengono chiamati i provider di servizi.  
  
-   I servizi che sono disponibili per altri VSPackage sono chiamati servizi globali.  
  
-   Servizi sono disponibili solo per i package VS che implementa o per qualsiasi oggetto che viene creato, sono denominati servizi locali.  
  
-   I servizi che sostituiscono i servizi incorporati o i servizi forniti da altri pacchetti, vengono chiamati servizio esegue l'override.  
  
-   Servizi o servizio esegue l'override, vengono caricato su richiesta, vale a dire il provider del servizio viene caricato quando viene richiesto il servizio che fornisce da un altro VSPackage.  
  
-   Per supportare il caricamento su richiesta, un provider del servizio registra i servizi globali con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per altre informazioni, vedere [Registrazione di servizi](../../misc/registering-services.md).  
  
-   Dopo aver ottenuto un servizio, utilizzare [QueryInterface](/visual-cpp/atl/queryinterface) \(codice non gestito\) o cast \(codice gestito\) per ottenere l'interfaccia desiderata, ad esempio:  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Codice gestito fa riferimento a un servizio per il tipo, mentre il codice non gestito fa riferimento a un servizio tramite il relativo GUID.  
  
-   Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Carica un pacchetto Visual Studio, passa un provider di servizi VSPackage per concedere l'accesso VSPackage ai servizi globali. Ciò è detto "posizione" VSPackage.  
  
-   Package VS può essere provider di servizi per gli oggetti creati. Ad esempio, un modulo potrebbe inviare una richiesta per un servizio di colore per il frame, che può passare la richiesta di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Gli oggetti gestiti che sono molto annidati o non individuati, possono chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per l'accesso diretto a servizi globali. Per altre informazioni, vedere [Procedura: Usare GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## Vedere anche  
 [Elenco dei servizi disponibili](../../extensibility/internals/list-of-available-services.md)   
 [Utilizzo e servizi](../../extensibility/using-and-providing-services.md)   
 [Cast e conversioni di tipi \(C\#\)](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Cast](/visual-cpp/cpp/casting)