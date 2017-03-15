---
title: Gestione dei package VS | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 35
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
ms.openlocfilehash: 32e4aa4302f7871e71907d094c12038b00d7e6bb
ms.lasthandoff: 02/22/2017

---
# <a name="managing-vspackages"></a>La gestione di VSPackage
Nella maggior parte dei casi non è necessario preoccuparsi di gestire i package VS, poiché i modelli di progetto e di elemento registrare e caricare automaticamente il pacchetto. Tuttavia, in alcuni casi potrebbe essere necessario apprendere un po' più per gestire il pacchetto.  
  
## <a name="using-the-experimental-instance"></a>Utilizzando l'istanza sperimentale  
 Per ulteriori informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Package VS della registrazione e annullamento della registrazione  
 Per ulteriori informazioni su come registrare e annullare la registrazione di VS e altri tipi di estensione, vedere [registrazione e annullamento della registrazione VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Caricamento di un VSPackage  
 Per caricare automaticamente quando una particolare che CMDUICONTEXT GUID è attivata, è possibile impostare i package VS. Per ulteriori informazioni, vedere [caricamento VS](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Utilizzo AsyncPackage per caricare in Background di VSPackage  
 La classe AsyncPackage consente pacchetto durante il caricamento in un thread in background per una migliore velocità di risposta dell'interfaccia utente in Visual Studio. Per ulteriori informazioni, vedere [procedura: utilizzare AsyncPackage ai package VS di caricamento in Background](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contesto dell'interfaccia utente basata su regole per le estensioni  
 Contesti dell'interfaccia utente basata su regole consente agli autori di estensione definire le condizioni esatte in cui viene attivato un contesto dell'interfaccia utente e caricamento VS associato. Per ulteriori informazioni, vedere [procedura: basate sulle regole di utilizzo di contesto dell'interfaccia utente per le estensioni di Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnosing-extension-performance"></a>Diagnosticare le prestazioni di estensione  
Estensioni possono influire sulle prestazioni di carico soluzione e di avvio. Informazioni su come viene calcolata impatto di estensione di Visual Studio e come poter analizzare localmente per verificare se un'estensione può essere visualizzata come alcun impatto sull'estensione delle prestazioni. Per ulteriori informazioni, vedere [procedura: diagnosticare le prestazioni di estensione](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshooting-vspackages"></a>Risoluzione dei problemi di VSPackage  
 Scopri le tecniche per la risoluzione dei problemi di package VS che non vengono caricati o segnalano errori: [VSPackage risoluzione dei problemi](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Package VS](../extensibility/internals/vspackages.md)
