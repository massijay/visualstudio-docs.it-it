---
title: "Scelta tra i package VS condivisi e con controllo delle versioni | Microsoft Docs"
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
  - "SxS"
  - "installazione side-by-side"
  - "installazione [Visual Studio SDK], side-by-side"
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Scelta tra i package VS condivisi e con controllo delle versioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Versioni diverse di Visual Studio possono coesistere nello stesso computer. Package VS può supportare qualsiasi combinazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versioni.  
  
 È possibile abilitare le installazioni side\-by\-side di VS con una delle due strategie, la strategia condivisa o la strategia di controllo delle versioni. Entrambi contenere la presenza di più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e associate le versioni di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Nella strategia condivisa, un VSPackage è registrato per l'utilizzo in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Nella strategia di controllo delle versioni, più DLL VSPackage sono installate, uno per ogni versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportati.  
  
## Package VS condivisi  
 Tramite un package VS condivisi è appropriato quando si utilizza la stessa VSPackage in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per implementare un package VS condivisi, è necessario eseguire i passaggi seguenti:  
  
-   Rendere il VSPackage compatibile con più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Due modalità di esecuzione sono pertanto disponibili:  
  
    -   Limitare il pacchetto Visual Studio per utilizzare solo le funzionalità della versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportati.  
  
    -   Programmare il VSPackage per adattarsi alla versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in cui è in esecuzione. Quindi, se le query per i servizi più recenti hanno esito negativo, il pacchetto Visual Studio può offrire altri servizi che sono supportati nelle versioni precedenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Registrare il pacchetto Visual Studio in modo appropriato. Per altre informazioni, vedere [Registrazione di VSPackage](../extensibility/internals/vspackage-registration.md) e [Managed VSPackage Registration](http://msdn.microsoft.com/it-it/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Registrare le estensioni dei file in modo appropriato. Per altre informazioni, vedere [Registrazione di estensioni di File per le distribuzioni Side\-By\-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Creare un programma di installazione che consente di distribuire il pacchetto Visual Studio per le versioni appropriate di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per altre informazioni, vedere [L'installazione di VS con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e [Gestione dei componenti](../extensibility/internals/component-management.md).  
  
-   Risolvere il problema dei conflitti di registrazione. Per altre informazioni, vedere [Registrazione di VSPackage](../extensibility/internals/vspackage-registration.md).  
  
-   Assicurarsi che i file con controllo delle versioni sia condivisi rispettino per consentire un'installazione sicura e rimozione di più versioni di conteggio dei riferimenti. Per altre informazioni, vedere [Gestione dei componenti](../extensibility/internals/component-management.md).  
  
## Package VS con controllo delle versioni  
 Sotto la strategia di VSPackage con controllo delle versioni, è creare un VSPackage per ogni versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportati. Questa operazione è appropriata quando si prevede di sfruttare i vantaggi dei servizi forniti dalle versioni più recenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], poiché ogni VSPackage può evolvere senza influire sulle altre. Tuttavia, la strategia di creazione di più file binari, da un unico codice base o da più basi di codice indipendenti, con controllo delle versioni può implicare più sviluppo iniziale di strategia condiviso. Inoltre, operazioni di configurazione aggiuntive potrebbero essere necessari perché è necessario creare un programma di installazione separato per ogni versione oppure un unico programma di installazione che rileva le versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che siano installati e che supporta il pacchetto Visual Studio.  
  
## Compatibilità binaria  
 In genere, la compatibilità binaria consente di VSPackage in codice nativo sviluppato con le versioni precedenti di Visual Studio per l'esecuzione in versioni successive di Visual Studio. Tuttavia, esistono tre importanti eccezioni:  
  
-   Se il pacchetto Visual Studio si basa su una particolare versione di common language runtime, quindi è necessario determinare in quale versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è in esecuzione.  
  
-   Un VSPackage potrebbe avere una dipendenza su una funzionalità specifica di un altro prodotto o un altro VSPackage. Di conseguenza, il package VS può essere eseguito solo in cui la dipendenza viene soddisfatta.  
  
-   Un pacchetto può essere influenzato da una correzione per la protezione in un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack o una versione successiva di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In questi casi, un VSPackage sviluppata con una versione precedente del [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] potrebbe non essere eseguito nelle versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dopo la correzione è stata applicata. Tuttavia, è possibile ricreare il pacchetto con la versione più recente ed eseguirla anche nelle versioni precedenti.  
  
 VSPackages gestito deve essere compilato utilizzando una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] che corrisponde alla versione di destinazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Oltre alla pianificazione per la compatibilità binaria per i file binari VSPackage, anche dovrebbe prendere in considerazione soluzioni e formati di file di progetto. Se il pacchetto Visual Studio crea un nuovo tipo di progetto, è necessario decidere se può essere eseguito in una sola versione o in più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per altre informazioni, vedere [Aggiornamento di progetti personalizzati](../misc/upgrading-custom-projects.md).  
  
## Vedere anche  
 [L'installazione di VS con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Gestione dei componenti](../extensibility/internals/component-management.md)