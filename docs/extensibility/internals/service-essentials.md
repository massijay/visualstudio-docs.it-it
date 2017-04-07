---
title: Servizio Essentials | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 8ff357d7ed3542a01cf8d98e36b9d0e99a122864
ms.lasthandoff: 04/05/2017

---
# <a name="service-essentials"></a>Servizio Essentials
Un servizio è un contratto tra due pacchetti VSPackage. Un VSPackage fornisce un set specifico di interfacce per un altro VSPackage da utilizzare. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]è una raccolta di VSPackage che forniscono servizi agli altri pacchetti VSPackage.  
  
 Ad esempio, è possibile utilizzare il servizio SVsActivityLog per ottenere un'interfaccia IVsActivityLog, che è possibile utilizzare per scrivere nel log attività. Per ulteriori informazioni, vedere [procedura: utilizzare il registro attività](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce inoltre alcuni servizi predefiniti che non sono registrati. Pacchetti VSPackage possono sostituire incorporati o altri servizi, fornendo l'override di un servizio. Sostituzione di un solo servizio è consentito per qualsiasi servizio.  
  
 Services non dispone di alcun tipo di individuazione. Pertanto, è necessario conoscere l'ID di servizio (SID) di un servizio che si desidera utilizzare e, è necessario conoscere quali interfacce fornisce. La documentazione di riferimento per il servizio fornisce queste informazioni.  
  
-   Pacchetti VSPackage che forniscono servizi vengono chiamati i provider di servizi.  
  
-   I servizi forniti da altri pacchetti VSPackage sono denominati servizi globali.  
  
-   Servizi sono disponibili solo per il pacchetto VSPackage che li implementa o per qualsiasi oggetto che viene creato, sono denominati servizi locali.  
  
-   Servizi che sostituiscono i servizi predefiniti o i servizi forniti da altri pacchetti, vengono chiamati servizio esegue l'override.  
  
-   I servizi o servizio esegue l'override, vengono caricato su richiesta, vale a dire, il provider del servizio viene caricato quando viene richiesto il servizio fornito da un altro VSPackage.  
  
-   Per supportare il caricamento su richiesta, un provider del servizio registra i servizi globali con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Per ulteriori informazioni, vedere [registrazione dei servizi](../../misc/registering-services.md).  
  
-   Dopo aver ottenuto un servizio, utilizzare [QueryInterface](/cpp/atl/queryinterface) (codice non gestito) o cast (codice gestito) per ottenere l'interfaccia desiderata, ad esempio:  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Codice gestito si riferisce a un servizio in base al tipo, mentre il codice non gestito si riferisce a un servizio con il relativo GUID.  
  
-   Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica un pacchetto VSPackage, passa un provider di servizi per il pacchetto VSPackage per consentire l'accesso VSPackage a servizi globali. Ciò è detto "posizione" il pacchetto VSPackage.  
  
-   Pacchetti VSPackage possono essere provider di servizi per gli oggetti creati. Ad esempio, un form potrebbe inviare una richiesta per un servizio di colore per il frame, che potrebbe passare alla richiesta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Gli oggetti gestiti che sono molto annidati, o non individuati, possono chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>per accedere direttamente ai servizi globali.</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Per ulteriori informazioni, vedere [procedura: usare GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco dei servizi disponibili](../../extensibility/internals/list-of-available-services.md)   
 [Utilizzando e servizi](../../extensibility/using-and-providing-services.md)   
 [Cast e conversioni di tipi](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Cast](/cpp/cpp/casting)
