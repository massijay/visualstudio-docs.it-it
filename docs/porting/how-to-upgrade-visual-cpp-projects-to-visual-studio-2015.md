---
title: "Procedura: Aggiornare i progetti Visual C++ a Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "progetti [C++], aggiornamento"
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: Aggiornare i progetti Visual C++ a Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si apre per la prima volta un progetto Visual C\+\+ creato in una versione precedente di Visual Studio, è possibile che venga richiesto di aggiornare il progetto. Nel messaggio viene chiesto se si desidera eseguire l'aggiornamento alla versione più recente del compilatore e delle librerie di Visual C\+\+. Le opzioni per l'aggiornamento dipendono dalla versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usata per creare il progetto.  
  
 È possibile usare [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] per aprire, modificare e compilare i progetti [!INCLUDE[win8](../debugger/includes/win8_md.md)] creati in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], ma per creare un nuovo progetto [!INCLUDE[win8](../debugger/includes/win8_md.md)], è necessario usare [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. Per creare un progetto [!INCLUDE[win81](../debugger/includes/win81_md.md)], è necessario usare [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)].  
  
 Per creare un progetto Windows 10, è necessario usare [!INCLUDE[vs_dev14](../msbuild/includes/vs_dev14_md.md)].  
  
 Se non viene richiesto di aggiornare il progetto, è possibile che non sia necessario eseguire alcun aggiornamento. Per altre informazioni, vedere [Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
-   Se il progetto \(con estensione VCPROJ\) è stato creato in una versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] precedente a [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], è necessario aggiornare il progetto.  
  
-   Se il progetto \(con estensione VCXPROJ\) è stato creato in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] o [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], sono disponibili due opzioni:  
  
    -   È possibile ignorare l'aggiornamento. In [!INCLUDE[vs_dev14](../msbuild/includes/vs_dev14_md.md)] verrà caricato il progetto senza apportare alcuna modifica se è disponibile l'accesso agli strumenti di Visual C\+\+ in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] con SP1, [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] o [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]. È possibile fornire questo accesso installando la versione di Visual Studio con cui il progetto è stato creato nello stesso computer in cui è presente [!INCLUDE[vs_dev14](../msbuild/includes/vs_dev14_md.md)]. Per altre informazioni, vedere [Installazione di versioni affiancate di Visual Studio](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md).  
  
    -   È possibile aggiornare il progetto consentendo a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di apportare le modifiche descritte più avanti in questo argomento. Se si dispone di più di un progetto Visual C\+\+ nella soluzione, è necessario aggiornali tutti.  
  
        > [!NOTE]
        >  Se si rifiuta l'aggiornamento alla prima richiesta, è possibile aggiornare il progetto in un secondo momento scegliendo **Aggiorna progetto VC\+\+** dal menu **Progetto**. Se il comando non viene visualizzato, non è necessario alcun aggiornamento.  
  
## Aggiornamento di un progetto Visual C\+\+  
 Se si consente a [!INCLUDE[vs_dev14](../msbuild/includes/vs_dev14_md.md)] di aggiornare automaticamente il progetto, vengono apportate queste modifiche:  
  
-   Il progetto viene modificato in modo da usare il compilatore e le librerie di [!INCLUDE[vs_dev14](../msbuild/includes/vs_dev14_md.md)] \(PlatformToolset \= VisualStudio v140\).  
  
-   Per i progetti [!INCLUDE[cppcli](../misc/includes/cppcli_md.md)] TargetFrameworkVersion viene impostato su .NET Framework 4.5.2.  
  
## Continuare a usare un set di strumenti della piattaforma personalizzato  
 Se si desidera continuare a usare un set di strumenti della piattaforma personalizzato in [!INCLUDE[vs_dev14](../msbuild/includes/vs_dev14_md.md)], il set di strumenti deve trovarsi in %Programmi%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ in un computer x86 o in %Programmi \(x86\)%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ in un computer x64. Per informazioni su come creare un set di strumenti della piattaforma personalizzato, vedere il post relativo al [multitargeting nativo per C\+\+](http://go.microsoft.com/fwlink/?LinkId=248587) nel blog del team di Visual C\+\+.  
  
## Vedere anche  
 [Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)