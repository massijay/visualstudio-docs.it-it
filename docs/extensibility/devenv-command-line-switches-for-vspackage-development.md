---
title: Opzioni della riga di comando devenv per lo sviluppo di VSPackage | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: 16
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ae42f7dd48a240f3d1c06c814834bc83c0cce75d
ms.lasthandoff: 02/22/2017

---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Opzioni della riga di comando devenv per lo sviluppo di VSPackage
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]consente agli sviluppatori di automatizzare le attività dalla riga di comando durante l'esecuzione di devenv.exe, il file che avvia l'ambiente di sviluppo integrato (IDE) di Visual Studio.  
  
 Le attività includono:  
  
-   Distribuzione di applicazioni in configurazioni predefinite all'esterno dell'IDE.  
  
-   Compilazione di progetti tramite set di impostazioni automaticamente le impostazioni di compilazione o configurazioni di debug.  
  
-   Caricamento dell'IDE in configurazioni specifiche, tutto da all'esterno dell'IDE. Inoltre, è possibile personalizzare l'IDE all'avvio.  
  
## <a name="guidelines-for-switches"></a>Linee guida per gli switch  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]documentazione vengono descritte le opzioni della riga di comando devenv a livello di utente. Per ulteriori informazioni, vedere [opzioni della riga di comando Devenv](../ide/reference/devenv-command-line-switches.md). Devenv supporta anche altre opzioni della riga di comando che sono utili con VSPackage sviluppo, distribuzione e debug.  
  
|Opzione della riga di comando|Descrizione|  
|--------------------------|-----------------|  
|/SafeMode|Avvia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in modalità provvisoria, caricando solo l'IDE predefinito e i servizi. L'opzione /safemode impedisce i package VS di terze parti di caricamento quando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene avviato, garantendo quindi un'esecuzione stabile.<br /><br /> Questa opzione non accetta argomenti.|  
|/resetskippkgs|Cancella tutti ignorare le opzioni di caricamento che sono stati aggiunti dagli utenti che desiderano evitare di caricare package VS problematico, quindi avvia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. La presenza di un tag SkipLoading disabilita il caricamento di un VSPackage. Cancellando il tag abilita nuovamente il caricamento del VSPackage.<br /><br /> Questa opzione non accetta argomenti.|  
|/rootsuffix|Avvia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizzando un percorso alternativo. Il seguente comando viene eseguito il collegamento creato dal [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] programma di installazione:<br /><br /> devenv /RootSuffix exp<br /><br /> In questo caso, exp identifica una posizione con un suffisso specifico, ad esempio 10.0Exp anziché 10.0. L'istanza sperimentale consente di eseguire il debug di un VSPackage separatamente dall'istanza di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che utilizza per scrivere codice.<br /><br /> Questa opzione può richiedere qualsiasi stringa che identifica un percorso a cui è stato creato con VSRegEx.exe. Per ulteriori informazioni, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).|  
|/Splash|Viene illustrato il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] schermata come di consueto e quindi viene visualizzata una finestra di messaggio prima che venga visualizzato l'IDE principale. La finestra di messaggio consente di esaminare la schermata iniziale, per cercare un'icona di prodotto VSPackage, ad esempio.<br /><br /> Questa opzione non accetta argomenti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta della riga di comando](../extensibility/adding-command-line-switches.md)   
 [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)
