---
title: "Procedura: debug di eccezioni ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, eccezioni"
  - "debug [Visual Studio], eccezioni ASP.NET"
  - "eccezioni, ASP.NET"
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: debug di eccezioni ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debug delle eccezioni è una parte importante dello sviluppo di una potente applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Per informazioni generali sul debug delle eccezioni, vedere [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Per eseguire il debug di eccezioni [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non gestite, è necessario assicurarsi che il debugger si interrompa ogni volta che ne raggiunge una.  Il runtime di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dispone di un gestore eccezioni di livello superiore.  Di conseguenza, per impostazione predefinita il debugger non si interrompe mai in corrispondenza di eccezioni non gestite.  Per interrompere il debugger quando viene generata un'eccezione, è necessario selezionare l'impostazione **Interrompi quando un'eccezione è: Generata** per tale eccezione nella finestra di dialogo **Eccezioni**.  
  
 Se Just My Code è attivato, la selezione dell'opzione **Interrompi quando un'eccezione è: Generata** non comporta l'interruzione immediata del debugger quando un'eccezione viene generata in un metodo .NET Framework o in un altro codice di sistema.  Invece l'esecuzione continua sino al raggiungimento di codice non di sistema, quindi si interrompe.  Non è pertanto necessario eseguire il codice di sistema quando si verifica un'eccezione.  
  
 Just My Code fornisce un'altra opzione che può rivelarsi molto utile: **Interrompi quando un'eccezione è: Non gestita dall'utente**.  Se si sceglie questa impostazione per un'eccezione, il debugger interromperà l'esecuzione nel codice utente, ma solo se l'eccezione non viene intercettata e gestita dal codice utente.  Questa impostazione annulla l'effetto del gestore eccezioni di primo livello di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], perché quest'ultimo si trova nel codice non utente.  
  
### Per attivare il debug delle eccezioni ASP.NET con Just My Code  
  
1.  Scegliere **Eccezioni** dal menu **Debug**.  
  
     Verrà visualizzata la finestra di dialogo **Eccezioni**.  
  
2.  Nella riga **Eccezioni Common Language Runtime** selezionare **Generata** o **Non gestita dall'utente**.  
  
     Per utilizzare l'impostazione **Non gestita dall'utente**, è necessario attivare **Solo codice utente**.  
  
### Procedure ottimali per la gestione delle eccezioni ASP.NET  
  
-   Collocare blocchi `try … catch` attorno al codice che può generare eccezioni anticipabili e gestibili.  Se, ad esempio, l'applicazione effettua chiamate a un Servizio Web XML o direttamente a SQL Server, il codice dovrebbe trovarsi in blocchi **try … catch** perché è possibile che si verifichino numerose eccezioni.