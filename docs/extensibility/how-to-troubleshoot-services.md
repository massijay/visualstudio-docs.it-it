---
title: "Procedura: risolvere i problemi relativi a servizi | Microsoft Docs"
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
  - "servizi, risoluzione dei problemi"
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: risolvere i problemi relativi a servizi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esistono alcuni problemi comuni che possono verificarsi quando si tenta di ottenere un servizio:  
  
-   Il servizio non è registrato con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Il servizio è richiesto dal tipo di interfaccia e non dal tipo di servizio.  
  
-   Il package VS che richiedono il servizio non è stato individuato.  
  
-   Viene utilizzato il provider di servizio non valido.  
  
 Se non è possibile ottenere il servizio richiesto, la chiamata a <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> restituisce null. È necessario verificare sempre null dopo la richiesta di un servizio:  
  
```c#  
IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog; if (log == null) return;  
```  
  
### Per risolvere i problemi relativi a un servizio  
  
1.  Esaminare il Registro di sistema per vedere se il servizio è stato registrato correttamente. Per altre informazioni, vedere [Registrazione di servizi](../misc/registering-services.md).  
  
     Nel seguente frammento di file con estensione reg viene illustrato come il servizio SVsTextManager potrebbe essere registrato:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
    ```  
  
     Nell'esempio precedente, il numero di versione è la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ad esempio 12.0 o 14.0, la chiave {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} è l'ID di servizio \(SID\) del servizio, SVsTextManager, e il valore predefinito {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} è il GUID della gestione testo VSPackage, che fornisce il servizio del pacchetto.  
  
2.  Quando si chiama GetService, utilizzare il tipo di servizio e non il tipo di interfaccia. Quando si richiede un servizio da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> estrae il GUID dal tipo. Un servizio non verrà trovato se sussistono le seguenti condizioni:  
  
    1.  Un tipo di interfaccia viene passato al metodo GetService anziché il tipo di servizio.  
  
    2.  Nessun GUID in modo esplicito viene assegnato all'interfaccia. Di conseguenza, il sistema crea un GUID predefinito per un oggetto in base alle esigenze.  
  
3.  Assicurarsi che il package VS che richiedono il servizio è stato individuato.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] siti un VSPackage al termine della creazione e prima di chiamare <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Se si dispone di codice in un costruttore di VSPackage che richiede un servizio, quindi spostare il metodo Initialize.  
  
4.  Assicurarsi che si utilizza il provider del servizio corretta.  
  
     Non tutti i provider di servizio sono simili. Il provider di servizi che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passa a una finestra degli strumenti è diversa da quella passa a un pacchetto. Il provider di servizi di finestra strumento conosce <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, ma non conosce <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. È possibile chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per ottenere un provider di servizi VSPackage all'interno di una finestra degli strumenti.  
  
     Se una finestra degli strumenti ospita un controllo utente o qualsiasi altro contenitore di controllo, il contenitore verrà individuato dal modello di componente di Windows e non sarà possibile accedere a qualsiasi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] servizi. È possibile chiamare <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> per ottenere un provider di servizi VSPackage da un contenitore di controlli.  
  
## Vedere anche  
 [Elenco dei servizi disponibili](../extensibility/internals/list-of-available-services.md)   
 [Utilizzo e servizi](../extensibility/using-and-providing-services.md)   
 [Funzionalità fondamentali del servizio](../extensibility/internals/service-essentials.md)