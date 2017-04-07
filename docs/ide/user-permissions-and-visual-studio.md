---
title: Autorizzazioni utente e Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: dc32236dad42ec169fc1c7a243b7c67fd5a8dbf3
ms.lasthandoff: 03/07/2017

---
# <a name="user-permissions-and-visual-studio"></a>Autorizzazioni utente e Visual Studio
Per motivi di sicurezza è necessario, quando possibile, eseguire Visual Studio come utente normale.  

> [!WARNING]
>  Accertarsi inoltre di non compilare, avviare o eseguire il debug di una soluzione di Visual Studio che non provenga da una persona o un percorso attendibile.  

 È possibile usare quasi tutte le funzioni dell'IDE di Visual Studio come utente normale, tuttavia è necessario disporre delle autorizzazioni di amministratore per completare le seguenti attività:  

|Area|Attività|Per altre informazioni|  
|----------|----------|--------------------------|  
|Installazione|Installare Visual Studio.|[Installare Visual Studio](../install/install-visual-studio.md)|  
||Installazione, aggiornamento o rimozione del contenuto della Guida locale.|[Installare e gestire il contenuto locale](../ide/install-and-manage-local-content.md)|  
|Tipi di applicazioni|Sviluppo di soluzioni per SharePoint.|[Requisiti per lo sviluppo di soluzioni SharePoint](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|  
||Acquisizione di una licenza per sviluppatori per [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Ottenere una licenza per sviluppatori (app di Windows Store)](http://go.microsoft.com/fwlink/?LinkID=241313)|  
|Casella degli strumenti|Aggiunta di controlli COM classici alla **Casella degli strumenti**.|[Uso della Casella degli strumenti](../ide/using-the-toolbox.md)|  
|Componenti aggiuntivi|Installazione e utilizzo di componenti aggiuntivi scritti tramite COM classico nell'IDE.|[Creazione di componenti aggiuntivi e di procedure guidate](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|  
|Compilazione|Utilizzo di eventi di post-compilazione che registrano un componente.|[Informazioni sulle istruzioni di compilazione personalizzate e sugli eventi di compilazione](/visual-cpp/ide/understanding-custom-build-steps-and-build-events)|  
||Aggiunta di un passaggio di registrazione durante la compilazione di progetti C++.|[Informazioni sulle istruzioni di compilazione personalizzate e sugli eventi di compilazione](/visual-cpp/ide/understanding-custom-build-steps-and-build-events)|  
|Debug|Debug di applicazioni eseguite con autorizzazioni elevate.|[Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)|  
||Debug di applicazioni eseguite con un account utente diverso, come i siti Web ASP.NET.|[Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|  
||Debug nell'area di sicurezza per applicazioni browser XAML (XBAP).|[Host WPF (PresentationHost.exe)](http://msdn.microsoft.com/Library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|  
||Utilizzo dell'emulatore per eseguire il debug di progetti di servizio cloud per Microsoft Azure.|[Debug di un servizio cloud in Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|  
||Configurazione di un firewall per il debug remoto.|[Debug remoto](../debugger/remote-debugging.md)|  
|Strumenti per le prestazioni|Profilatura di un'applicazione.|[Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md)|  
|Distribuzione|Distribuzione di un'applicazione Web in Internet Information Services (IIS) su un computer locale.|[Deploying an ASP.NET Web Application to a Hosting Provider using Visual Studio or Visual Web Developer: Deploying to IIS as a Test Environment](http://go.microsoft.com/fwlink/?LinkId=266478) (Distribuzione di un'applicazione Web ASP.NET a un provider di hosting usando Visual Studio o Visual Web Developer: distribuzione a IIS come ambiente di test)|

## <a name="running-visual-studio-as-an-administrator"></a>Esecuzione di Visual Studio come amministratore  
 È possibile avviare Visual Studio con autorizzazioni amministrative ogni volta che si avvia l'IDE oppure modificare il collegamento dell'applicazione in modo che venga eseguita sempre con autorizzazioni amministrative. Per altre informazioni, vedere la Guida di Windows.  

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8debuggerincludeswin8mdmd-includewin81debuggerincludeswin81mdmd-includewinserver8debuggerincludeswinserver8mdmd-or-includewinblueserver2ideincludeswinblueserver2mdmd"></a>Per eseguire Visual Studio con autorizzazioni amministrative in [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[win81](../debugger/includes/win81_md.md)], [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] o [!INCLUDE[winblue_server_2](../ide/includes/winblue_server_2_md.md)]  

1.  Nella schermata **iniziale** digitare **Visual Studio**. Verrà visualizzata la versione o le versioni di Visual Studio installate.  

2.  Selezionare la versione di Visual Studio che si desidera avviare, quindi visualizzare il menu di scelta rapida (nella parte inferiore dello schermo). Scegliere **Esegui come amministratore**.  

     All'avvio di Visual Studio, viene visualizzato **(Amministratore)** dopo il nome del prodotto nella barra del titolo.  

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7debuggerincludeswin7mdmd-or-includewinsvr08r2debuggerincludeswinsvr08r2mdmd"></a>Per eseguire Visual Studio con autorizzazioni amministrative in [!INCLUDE[win7](../debugger/includes/win7_md.md)] o [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]  

1.  Dal menu **Start** scegliere **Tutti i programmi**.  

2.  Nella cartella **Microsoft Visual Studio** *Versione* selezionare **Visual Studio** *Versione*, aprire il menu di scelta rapida e quindi selezionare **Esegui come amministratore**.  

     All'avvio di Visual Studio, viene visualizzato **(Amministratore)** dopo il nome del prodotto nella barra del titolo.  

## <a name="see-also"></a>Vedere anche  
 [Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [Installare Visual Studio](../install/install-visual-studio.md)

