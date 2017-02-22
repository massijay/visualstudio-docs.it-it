---
title: "Build Loggers | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, writing loggers"
  - "MSBuild, logging"
  - "logging [MSBuild]"
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Build Loggers
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I logger offrono un metodo per personalizzare l'output della compilazione e visualizzare messaggi, errori o avvisi in risposta a specifici eventi di compilazione.  Ogni logger viene implementato come classe .NET che implementa l'interfaccia <xref:Microsoft.Build.Framework.ILogger>, definita nell'assembly Microsoft.Build.Framework.dll.  
  
 Per implementare un logger, è possibile utilizzare due diversi metodi:  
  
-   Implementare direttamente l'interfaccia <xref:Microsoft.Build.Framework.ILogger>.  
  
-   Derivare la classe dalla classe di supporto <xref:Microsoft.Build.Utilities.Logger>, definita nell'assembly Microsoft.Build.Utilities.dll.  L'oggetto <xref:Microsoft.Build.Utilities.Logger> implementa <xref:Microsoft.Build.Framework.ILogger> e fornisce le implementazioni predefinite di alcuni membri di <xref:Microsoft.Build.Framework.ILogger>.  
  
 In questo argomento viene illustrato come scrivere un semplice logger che deriva dalla classe <xref:Microsoft.Build.Utilities.Logger> e visualizza i messaggi sulla console come risposta a determinati eventi di compilazione.  
  
## Registrazione per gli eventi  
 Lo scopo di un logger è di raccogliere le informazioni sull'avanzamento della compilazione, come segnalato dal modulo di gestione della compilazione, e di riportare queste informazioni in maniera utile.  Tutti i logger devono eseguire l'override del metodo <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>, ovvero la posizione in cui il logger effettua la registrazione per gli eventi.  Nell'esempio riportato di seguito il logger effettua la registrazione per gli eventi <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 [!code-cs[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## Risposta a eventi  
 Ora il logger è registrato per eventi specifici e dovrà gestire tali eventi quando questi si verificano.  Per gli eventi <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>, il logger scrive semplicemente una breve frase e il nome del file di progetto implicato nell'evento.  Tutti i messaggi provenienti dal logger vengono scritti nella finestra della console.  
  
 [!code-cs[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## Risposta ai valori di dettaglio del logger  
 In alcuni casi può essere utile registrare le informazioni di un evento solo se l'opzione opzione **\/verbosity** di MSBuild.exe contiene un determinato valore.  In questo esempio il gestore dell'evento <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> registra un messaggio solo se la proprietà <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>, impostata dall'opzione **\/verbosity**, è uguale a <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed`.  
  
 [!code-cs[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## Specifica di un logger  
 Una volta compilato il logger in un assembly, è necessario specificare in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per utilizzare tale logger durante le compilazioni.  Questa operazione viene eseguita utilizzando l'opzione **\/logger** con MSBuild.exe.  Per ulteriori informazioni sulle opzioni disponibili per MSBuild.exe, vedere [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
 La seguente riga di comando compila il progetto `MyProject.csproj` e utilizza la classe logger implementata in `SimpleLogger.dll`.  L'opzione **\/nologo** nasconde l'intestazione e il messaggio del copyright, mentre l'opzione **\/noconsolelogger** disattiva il logger di console predefinito di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 La seguente riga di comando compila il progetto con lo stesso logger, ma con un livello di `Verbosity` specificato come `Detailed`.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## Esempio  
  
### Descrizione  
 L'esempio riportato di seguito contiene il codice completo per il logger.  
  
### Codice  
 [!code-cs[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
### Commenti  
  
## Esempio  
  
### Descrizione  
 Nell'esempio riportato di seguito viene illustrata l'implementazione di un logger che scrive il log in un file anziché visualizzarlo nella finestra di console.  
  
### Codice  
 [!CODE [msbuild_BasicLogger#1](../CodeSnippet/VS_Snippets_Misc/msbuild_BasicLogger#1)]  
  
### Commenti  
  
## Vedere anche  
 [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)