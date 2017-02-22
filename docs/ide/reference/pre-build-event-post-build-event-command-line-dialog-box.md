---
title: "Finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEventsBuilder"
  - "vb.ProjectPropertiesBuildEventsBuilder"
helpviewer_keywords: 
  - "$(SolutionExt)"
  - "$(ProjectDir)"
  - "$(TargetPath)"
  - "$(ProjectExt)"
  - "$(TargetFileName)"
  - "$(PlatformName)"
  - "$(SolutionName)"
  - "macro, eventi di compilazione"
  - "$(SolutionPath)"
  - "$(ProjectPath)"
  - "$(ProjectFileName)"
  - "$(DevEnvDir)"
  - "$(TargetName)"
  - "$(TargetDir)"
  - "$(SolutionDir)"
  - "$(TargetExt)"
  - "$(OutDir)"
  - "$(ConfigurationName)"
  - "$(SolutionFileName)"
  - "$(ProjectName)"
  - "eventi di compilazione, macro"
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È possibile digitare gli eventi pre\-compilazione o post\-compilazione per la [Pagina Eventi di compilazione, Progettazione progetti \(C\#\)](../../ide/reference/build-events-page-project-designer-csharp.md) direttamente nella casella di modifica oppure selezionare macro pre\-compilazione e post\-compilazione dall'elenco di macro disponibili.  
  
> [!NOTE]
>  Gli eventi pre\-compilazione non vengono eseguiti se il progetto è aggiornato e non viene attivata la compilazione.  
  
## Elenco degli elementi dell'interfaccia utente  
 **Casella di modifica della riga di comando**  
 Contiene gli eventi da eseguire per la pre\-compilazione o la post\-compilazione.  
  
> [!NOTE]
>  Aggiungere un'istruzione `call` prima di tutti i comandi di post\-compilazione che eseguono file BAT.  Ad esempio, `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Macro**  
 Espande la casella di modifica per visualizzare l'elenco delle macro che è possibile inserire nella casella di modifica della riga di comando.  
  
 **Tabella delle macro**  
 Elenca le macro disponibili e i relativi valori.  Vedere la sezione "Macro" seguente per una descrizione di ogni macro.  È possibile selezionare una sola macro alla volta da inserire nella casella di modifica della riga di comando.  
  
 **Insert**  
 Inserisce nella casella di modifica della riga di comando la macro selezionata nella tabella delle macro.  
  
### Macro  
 È possibile utilizzare le macro desiderate per specificare i percorsi dei file oppure per ottenere il nome effettivo del file di input in presenza di più selezioni.  Per queste macro non viene effettuata la distinzione tra maiuscole e minuscole.  
  
|Macro|Descrizione|  
|-----------|-----------------|  
|`$(ConfigurationName)`|Il nome della configurazione del progetto corrente, ad esempio "Debug".|  
|`$(OutDir)`|Il percorso della directory dei file di output relativi alla directory del progetto.  Si risolve nel valore relativo alla proprietà Directory di output.  Include la barra rovesciata finale "\\".|  
|`$(DevEnvDir)`|La directory di installazione di Visual Studio \(definito da unità e il percorso\); include la barra rovesciata "\\" finale.|  
|`$(PlatformName)`|Il nome della piattaforma di destinazione corrente.  Ad esempio, "AnyCPU".|  
|`$(ProjectDir)`|La directory del progetto \(definita con unità e percorso\). Include la barra rovesciata "\\" finale.|  
|`$(ProjectPath)`|Il nome del percorso assoluto del progetto \(definito con unità, percorso, nome di base ed estensione file\).|  
|`$(ProjectName)`|Nome di base del progetto.|  
|`$(ProjectFileName)`|Il nome file del progetto \(definito con nome di base ed estensione file\).|  
|`$(ProjectExt)`|Estensione di file del progetto.  È incluso il punto '.' prima dell'estensione.|  
|`$(SolutionDir)`|La directory della soluzione \(definita con unità e percorso\). Include la barra rovesciata "\\" finale.|  
|`$(SolutionPath)`|Il nome del percorso assoluto della soluzione \(definito con unità, percorso, nome di base ed estensione file\).|  
|`$(SolutionName)`|Nome di base della soluzione.|  
|`$(SolutionFileName)`|Il nome file della soluzione \(definito con nome di base ed estensione file\).|  
|`$(SolutionExt)`|Estensione di file della soluzione.  È incluso il punto '.' prima dell'estensione.|  
|`$(TargetDir)`|La directory del file di output principale per la compilazione \(definita con unità e percorso\).  Include la barra rovesciata finale "\\".|  
|`$(TargetPath)`|Il nome del percorso assoluto del file di output principale per la compilazione \(definito con unità, percorso, nome di base ed estensione file\).|  
|`$(TargetName)`|Il nome di base del file di output principale per la compilazione.|  
|`$(TargetFileName)`|Il nome file del file di output principale per la compilazione \(definito come nome di base ed estensione file\).|  
|`$(TargetExt)`|L'estensione file del file di output principale per la compilazione.  È incluso il punto '.' prima dell'estensione.|  
  
## Vedere anche  
 [Specifica di eventi di compilazione personalizzati in Visual Studio](../../ide/specifying-custom-build-events-in-visual-studio.md)   
 [Pagina Eventi di compilazione, Progettazione progetti \(C\#\)](../../ide/reference/build-events-page-project-designer-csharp.md)   
 [Procedura: specificare gli eventi di compilazione \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Procedura: specificare eventi di compilazione \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)