---
title: "Installazione di versioni affiancate di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installazioni affiancate [Visual Studio]"
  - "Guida [Visual Studio], installazione"
  - "Express Edition [Visual Studio]"
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
caps.handback.revision: 47
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Installazione di versioni affiancate di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile installare questa versione di Visual Studio in un computer in cui è già installata una versione precedente. Se si verifica un errore di installazione, è possibile usare lo [strumento di raccolta dei log](http://go.microsoft.com/fwlink/?LinkId=262077) per raccogliere informazioni sugli errori per poter eseguire il debug dei problemi manualmente.  
  
> [!NOTE]
>  Si consiglia di installare le versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nell'ordine nel quale vengono rilasciate. Ad esempio, installare Visual Studio 2013 prima di installare Visual Studio 2015.  
  
 Prima di installare le versioni affiancate, verificare le seguenti condizioni:  
  
-   Se si usa Visual Studio 2015 per aprire una soluzione creata in [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], successivamente è possibile aprire e modificare nuovamente la soluzione nella versione precedente purché non sia stata implementata alcuna funzionalità specifica di Visual Studio 2015.  
  
-   Se si prova a usare Visual Studio 2015 per aprire una soluzione creata in [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] o in una versione precedente, potrebbe essere necessario modificare i progetti e i file per renderli compatibili con Visual Studio 2015. Per altre informazioni, vedere [Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
-   Se si disinstalla una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da un computer in cui sono installate più versioni, le associazioni di file per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verranno rimosse per tutte le versioni. È possibile eseguire di nuovo il mapping di queste associazioni di file tramite il pulsante **Ripristina associazioni file** in **Ambiente** nella pagina **Generale** della finestra di dialogo [Opzioni](../ide/reference/general-environment-options-dialog-box.md).  
  
-   Visual Studio non aggiorna automaticamente le estensioni, perché non tutte le estensioni sono compatibili. È necessario reinstallare le estensioni da [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=178891) o dall'autore del software.  
  
## Versioni di .NET Framework e installazioni affiancate  
  
-   I progetti Visual Basic, Visual C\# e Visual F\# usano l'opzione **Framework di destinazione** in **Creazione progetti** per specificare la versione di .NET Framework da usare. Per un progetto C\+\+ è possibile modificare manualmente il framework di destinazione modificando il file con estensione vcxproj. Per altre informazioni, vedere [Compatibilità tra versioni](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md).  
  
     Quando si crea un progetto, è possibile specificare a quale versione di .NET Framework è destinato il progetto nell'elenco **.NET Framework** della finestra di dialogo **Nuovo progetto**.  
  
     Per informazioni specifiche del linguaggio, vedere l'argomento corrispondente nella tabella seguente.  
  
    |Linguaggio|Argomento|  
    |----------------|---------------|  
    |[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]|[Pagina Applicazione, Creazione progetti \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C\#|[Applicazione \(pagina\), Creazione progetti \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F\#|[Configuring Projects](../Topic/Configuring%20Projects%20\(F%23\).md)|  
    |C\+\+|[Procedura: modificare il framework di destinazione e il set di strumenti della piattaforma](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md)|  
    |[!INCLUDE[jsprjscript](../debugger/debug-interface-access/includes/jsprjscript_md.md)]|[Esecuzione di un'applicazione JScript su una versione precedente di Common Language Runtime](http://msdn.microsoft.com/it-it/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## Vedere anche  
 [Installazione di Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)   
 [Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Compatibilità tra versioni](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md)   
 [Installazione di più versioni in lingue diverse di Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [Compilazione di applicazioni isolate C\/C\+\+ e di assembly side\-by\-side](/visual-cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies)   
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3)