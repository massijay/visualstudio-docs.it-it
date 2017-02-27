---
title: "WPF MSBuild Task Reference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "WPF MSBuild task reference [WPF MSBuild], term/definition table"
  - "build tasks [WPF MSBuild], Microsoft build engine"
  - "build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources"
  - "WPF MSBuild task reference [WPF MSBuild]"
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# WPF MSBuild Task Reference
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il processo di compilazione di Windows Presentation Foundation \(WPF\) estende il motore di compilazione Microsoft \(MSBuild\) con un insieme aggiuntivo di attività di compilazione, incluse le attività per compilare markup ed elaborare risorse.  
  
## In questa sezione  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Classifica un insieme di risorse di origine come quelle che verranno incorporate in un assembly.  Se una risorsa non è localizzabile, viene incorporata nell'assembly dell'applicazione principale; in caso contrario, viene incorporata in un assembly satellite.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Genera un assembly se almeno una pagina [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] in un progetto fa riferimento a un tipo dichiarato localmente in tale progetto.  L'assembly generato viene rimosso dopo il completamento del processo di compilazione o in caso di suo esito negativo.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Restituisce la directory del runtime [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] corrente.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Converte i file di progetto [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] non localizzabili in formato binario compilato.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Esegue la compilazione del markup del secondo passaggio sui file [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] che fanno riferimento ai tipi nello stesso progetto.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Unisce i commenti e gli attributi di localizzazione di uno o più file in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] in un singolo file per l'intero assembly.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Incorpora una o più risorse \(.jpg, .ico, .bmp, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] in formato binario e altri tipi di estensione\) in un file .resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Controlla, aggiorna o rimuove gli identificatori univoci \(UID\) per localizzare tutti gli elementi [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] inclusi nei file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] di origine.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Aggiunge l'elemento  **\< il hostInBrowser \/\>** al manifesto dell'applicazione \(*nomeprogetto*.exe.manifest\) quando viene compilato un progetto [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  
  
## Vedere anche  
 [MSBuild](http://msdn.microsoft.com/it-it/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)