---
title: "Procedura: Risolvere i problemi relativi agli aggiornamenti di progetti Visual Studio con esito negativo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisualStudio.SourceControl.CannotOpenFromSourceControlDSW"
  - "vs.UpgradeProjectSolution.8.0"
helpviewer_keywords: 
  - "aggiornamento di applicazioni, Visual Studio"
  - "aggiornamento di progetti [Visual Studio]"
  - "progetti [Visual Studio], aggiornamento"
  - "Conversione guidata di Visual Studio"
  - "Conversione guidata"
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 30
caps.handback.revision: 30
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Procedura: Risolvere i problemi relativi agli aggiornamenti di progetti Visual Studio con esito negativo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Talvolta Visual Studio non è in grado di convertire completamente un progetto da una versione precedente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Se i suggerimenti nelle sezioni seguenti non risolvono il problema specifico, è possibile trovare ulteriori informazioni su Technet [Wiki: portale di sviluppo](http://go.microsoft.com/fwlink/?LinkId=254808).  
  
## Impossibile eseguire il progetto poiché non è stato individuato alcun file  
 Un file di progetto contiene percorsi di file hard\-coded che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizza per eseguire il progetto quando si preme F5.  Questi percorsi possono includere la posizione del file devenv.exe e di altri file necessari.  In una versione aggiornata di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], i percorsi di questi file possono essere modificati.  
  
#### Per risolvere percorsi file errati  
  
1.  Aprire il file di progetto in un editor di testo.  
  
2.  Analizzare i percorsi file che potrebbero essere errati, in particolare quelli che contengono un numero di versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Modificare i percorsi file errati in modo che puntino alle nuove destinazioni.  
  
## Impossibile compilare il progetto per mancanza di riferimenti validi  
 Quando si aggiorna [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è anche possibile aggiornare la versione [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Se il progetto contiene riferimenti non più utilizzati nella versione più recente di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], tali riferimenti potrebbero non essere risolti correttamente.  Questa condizione potrebbe riguardare in particolare i riferimenti che includono numeri di versione, ad esempio `Microsoft.VisualStudio.Shell.Interop.8.0`.  
  
 Se il codice presenta molti riferimenti non validi, la soluzione più semplice potrebbe essere quella di utilizzare la funzionalità multitargeting di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di individuare una versione precedente di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### Per risolvere riferimenti errati  
  
1.  Aprire il file di progetto in un editor di testo.  
  
2.  Aprire la pagina delle proprietà del progetto.  
  
3.  Selezionare il valore corretto **Framework di destinazione**.  In alternativa, è possibile modificare il valore dell'elemento `<TargetFrameworkVersion>` direttamente nel file di progetto.  
  
 Se si desidera eseguire il progetto nella versione aggiornata di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], è necessario aggiornare i riferimenti per il progetto e qualsiasi istruzione `Imports` o `Using` che chiama i riferimenti.  Se il progetto viene caricato nell'IDE, è possibile aggiornare i riferimenti tramite **Esplora soluzioni** o la finestra di dialogo **Gestione riferimenti**.  
  
## Vedere anche  
 [\/Upgrade](../ide/reference/upgrade-devenv-exe.md)   
 [Converting to ASP.NET 4](../Topic/Converting%20to%20ASP.NET%204.md)