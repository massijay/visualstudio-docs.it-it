---
title: Visual Studio SDK | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 56
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: b3cd444e48893057a057c39c515e51ff8b509b34
ms.lasthandoff: 03/07/2017

---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK consente di estendere le funzionalità di Visual Studio o integrare le nuove funzionalità in Visual Studio. È possibile distribuire le estensioni ad altri utenti, nonché per Visual Studio Gallery. Di seguito sono illustrati alcuni dei modi in cui si può estendere Visual Studio:  
  
-   Aggiungere i comandi, pulsanti, menu e altri elementi dell'interfaccia utente dell'IDE  
  
-   Aggiungere finestre degli strumenti per la nuova funzionalità  
  
-   Estendere IntelliSense per una lingua specifica, o fornire IntelliSense per i nuovi linguaggi di programmazione  
  
-   Utilizzare le lampadine per fornire suggerimenti che consentono agli sviluppatori di scrivere codice migliore  
  
-   Abilitare il supporto per un nuovo linguaggio  
  
-   Aggiungere un tipo di progetto personalizzato  
  
-   Raggiungere milioni di sviluppatori tramite Visual Studio Gallery  
  
 Se non ha mai scritto un'estensione di Visual Studio prima, si devono trovare ulteriori informazioni su queste funzionalità e a [iniziare a sviluppare estensioni di Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>L'installazione di Visual Studio SDK  
 Visual Studio SDK è una funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Novità di Visual Studio 2017 SDK  
 Visual Studio SDK dispone di alcune nuove funzionalità quali il supporto di carico soluzione Lightweight e il formato v3 VSIX, nonché modifiche che potrebbero essere necessario aggiornare l'estensione di rilievo. Per ulteriori informazioni, vedere [novità di Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Linee guida sull'esperienza utente di Visual Studio  
 Ottenere suggerimenti per la progettazione dell'interfaccia utente per l'estensione in [linee guida esperienza utente di Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 È inoltre possibile imparare a migliorare l'aspetto in dispositivi con DPI elevati con l'estensione nostro [Addressing problemi DPI](../extensibility/addressing-dpi-issues2.md) argomento.  
  
 Sfruttare il [servizio immagini e catalogo](../extensibility/image-service-and-catalog.md) per la gestione delle immagini eccezionale e supporto per valori DPI elevati e temi.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Ricerca e installazione delle estensioni di Visual Studio esistenti  
 È possibile trovare le estensioni di Visual Studio nel **estensioni e aggiornamenti** nella finestra di dialogo di **strumenti** menu. Per ulteriori informazioni, vedere [ricerca e utilizzo delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). È anche possibile trovare estensioni nel [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Riferimento al SDK di Visual Studio  
 È possibile trovare il riferimento API di Visual Studio SDK a [riferimenti di Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Esempi di Visual Studio SDK  
 È possibile trovare esempi di origine aperto delle estensioni di Visual Studio SDK su GitHub all'indirizzo [esempi di Visual Studio](https://aka.ms/vs2015sdksamples). Questo archivio GitHub è inclusi esempi che illustrano varie funzionalità estendibili in Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Altre risorse di Visual Studio SDK  
 Se si domande su VSSDK o si desidera condividere le proprie esperienze di sviluppo di estensioni, è possibile utilizzare il [forum sull'estendibilità di Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) o [tale Group Chat](https://gitter.im/Microsoft/extendvs).  
  
 È possibile trovare altre informazioni, vedere il [Arcana VSX blog](http://blogs.msdn.com/b/vsx/) e un numero di blog scritti dai Microsoft MVPs:  
  
-   [Estensioni di Visual Studio preferito](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Extensibility di Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Estensione di Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [Domande frequenti: Conversione di componenti aggiuntivi in estensioni VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [La gestione di più thread in codice gestito](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Estensione menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [Aggiunta di comandi alle barre degli strumenti](../extensibility/adding-commands-to-toolbars.md)   
 [Estensione e personalizzazione di finestre degli strumenti](../extensibility/extending-and-customizing-tool-windows.md)   
 [Editor e le estensioni del servizio di linguaggio](../extensibility/editor-and-language-service-extensions.md)   
 [Estensione di progetti](../extensibility/extending-projects.md)   
 [Opzioni e impostazioni utente estensione](../extensibility/extending-user-settings-and-options.md)   
 [Creazione di progetto personalizzati e modelli di elemento](../extensibility/creating-custom-project-and-item-templates.md)   
 [Estensione di proprietà e la finestra proprietà](../extensibility/extending-properties-and-the-property-window.md)   
 [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Utilizzo e servizi](../extensibility/using-and-providing-services.md)   
 [La gestione di VSPackage](../extensibility/managing-vspackages.md)   
 [Visual Studio isolato Shell](../extensibility/visual-studio-isolated-shell.md)   
 [Distribuzione di estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [All'interno di Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Supporto per Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archivio](../extensibility/archive.md)   
 [Riferimenti su Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
