---
title: "RC Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions"
  - "vc.task.rc"
  - "VC.Project.VCResourceCompilerTool.SuppressStartupBanner"
  - "VC.Project.VCResourceCompilerTool.NullTerminateStrings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "RC task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), RC task"
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# RC Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esegue il wrapping dello strumento compilatore di risorse di Microsoft Windows, rc.exe.  L'attività **RC** compila le risorse, come ad esempio cursori, icone, bitmap, finestre di dialogo e tipi di carattere in un file di risorse \(res\).  Per ulteriori informazioni, vedere "Compilatore di risorse" sul sito Web di [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività RC.  La maggior parte dei parametri dell'attività e alcuni set di parametri, corrispondere a un'opzione della riga di comando.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Parametro **String\[\]** facoltativo.<br /><br /> Aggiunge una directory all'elenco di directory in cui viene eseguita la ricerca dei file di inclusione.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/I** in [Utilizzo di RC \(Riga di comando RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(la pagina potrebbe essere in inglese\) sul sito Web MSDN.|  
|**AdditionalOptions**|Parametro **String** facoltativo.<br /><br /> Un elenco di esempio dell'optionsor della riga di comando, **"***\/option1 \/option2 \/option\#*".  Utilizzare questo parametro per specificare opzioni della riga di comando che non sono rappresentate da qualsiasi altro parametro dell'attività **RC**.<br /><br /> Per ulteriori informazioni, vedere le opzioni in [Using RC \(The RC Command Line\) sul sito WEB MSDN](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**Culture**|Parametro **String** facoltativo.<br /><br /> Specifica un ID delle impostazioni locali che rappresenta le impostazioni cultura utilizzate nella risorsa.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/l** in [Utilizzo di RC \(Riga di comando RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(la pagina potrebbe essere in inglese\) sul sito Web MSDN.|  
|**IgnoreStandardIncludePath**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, non consente il controllo della variabile di ambiente INCLUDE da parte del compilatore di risorse quando cerca i file di intestazione o file di risorse.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/x** in [Utilizzo di RC \(Riga di comando RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(la pagina potrebbe essere in inglese\) sul sito Web MSDN.|  
|**NullTerminateStrings**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, null termina tutte le stringhe nella tabella di stringhe.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/n** in [Utilizzo di RC \(Riga di comando RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(la pagina potrebbe essere in inglese\) sul sito Web MSDN.|  
|**PreprocessorDefinitions**|Parametro **String\[\]** facoltativo.<br /><br /> Definire uno o più simboli del preprocessore per il compilatore di risorse.  Specificare un elenco di simboli della macro.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/d** in [Utilizzo di RC \(Riga di comando RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(la pagina potrebbe essere in inglese\) sul sito Web MSDN.  Vedere anche **UndefinePreprocessorDefinitions** in questa tabella.|  
|**ResourceOutputFileName**|Parametro **String** facoltativo.<br /><br /> Specifica il nome del file di risorse.  Specificare un nome del file di risorse.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/fo** in [Utilizzo di RC \(Riga di comando RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(la pagina potrebbe essere in inglese\) sul sito Web MSDN.|  
|**ShowProgress**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, visualizza messaggi che riportano sullo stato di avanzamento del compilatore.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/v** in [Utilizzo di RC \(Riga di comando RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(la pagina potrebbe essere in inglese\) sul sito Web MSDN.|  
|**Source**|Parametro `ITaskItem[]` obbligatorio.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere utilizzato ed emesso dalle attività.|  
|**SuppressStartupBanner**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del copyright e il messaggio del numero di versione quando l'attività inizia.<br /><br /> Per ulteriori informazioni, digitare l'opzione della riga di comando **\/?**, quindi vedere l'opaione \(**\/nologo**\).|  
|**TrackerLogDirectory**|Parametro **String** facoltativo.<br /><br /> Specifica la directory del log dello strumento di rilevamento.|  
|**UndefinePreprocessorDefinitions**|Rimuovere la definizione di un simbolo del preprocessore.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/u** in [Utilizzo di RC \(Riga di comando RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) \(la pagina potrebbe essere in inglese\) sul sito Web MSDN.  Vedere anche **PreprocessorDefinitions** in questa tabella.|  
  
## Note  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)