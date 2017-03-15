---
title: "JIT, Debug, Finestra di dialogo Opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Debugger.JIT"
  - "vs.debug.options.JIT"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debug JIT, impostazione opzioni"
  - "Finestra di dialogo Opzioni, debug"
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# JIT, Debug, Finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per accedere alla pagina **JIT**, scegliere **Opzioni** dal menu **Strumenti**.  Nella finestra di dialogo **Opzioni** espandere il nodo **Debug** e selezionare **JIT**.  Questa pagina consente di abilitare il debug JIT per codice gestito, codice nativo e script.  Per ulteriori informazioni, vedere [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 È possibile abilitare il debug JIT per questi tipi di programma:  
  
-   Gestito  
  
-   Nativo  
  
-   Script  
  
 Il debug JIT è una tecnica per il debug di un programma avviato al di fuori di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  È possibile eseguire un programma creato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] al di fuori dell'ambiente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Se il debug JIT è abilitato e si verifica un arresto anomalo, viene visualizzata una finestra di dialogo in cui viene chiesto se si desidera eseguire il debug.  
  
## Avvisi associati  
 Quando si accede a questa pagina della finestra di dialogo **Opzioni**, è possibile che venga visualizzato il seguente messaggio di avviso:  
  
 **Un altro debugger è stato registrato come debugger JIT.  Per risolvere il problema, abilitare il debug JIT o ripristinare Visual Studio.**  
  
 Questo messaggio viene visualizzato se come debugger JIT è impostato un altro debugger, ad esempio una versione precedente del debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 È anche possibile che venga visualizzato il messaggio seguente:  
  
 **Rilevati errori di registrazione del debug JIT.  Per risolvere il problema, abilitare il debug JIT o ripristinare Visual Studio.**  
  
 In entrambi i casi, finché il problema non viene risolto, per l'esecuzione del debug JIT con [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] sarà necessario disporre dei privilegi di amministratore.  Se si tenta di abilitare la modalità JIT in queste condizioni senza disporre di questi privilegi, viene visualizzato il seguente messaggio di errore:  
  
 **Accesso negato.  Chiedere a un amministratore di abilitare il debug JIT o ripristinare l'installazione di Visual Studio.**  
  
## Vedere anche  
 [Debug, finestra di dialogo Opzioni](../debugger/debugging-options-dialog-box.md)   
 [Procedura: specificare le impostazioni del debugger](../debugger/how-to-specify-debugger-settings.md)