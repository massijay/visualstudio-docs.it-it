---
title: "XDCMake Task | Microsoft Docs"
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
  - "vc.task.xdcmake"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "XDCMake task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), XDCMake task"
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XDCMake Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esegue il wrapping dello strumento della Documentazione XML \(xdcmake.exe\) che unisce i file di commento \(.xdc\) del documento XML in un file con estensione xml.  
  
 Un file xdc viene creato quando si forniscono commenti relativi alla documentazione nel codice sorgente di Visual C\+\+ e compila tramite l'opzione del compilatore [\/doc](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp).  Per informazioni dettagliate,  vedere [Riferimento a XDCMake](/visual-cpp/ide/xdcmake-reference), [Pagina delle proprietà dello strumento generatore di documenti XML](/visual-cpp/ide/xml-document-generator-tool-property-pages) e la Guida della riga di comando \(**\/?**\) per xdcmake.exe.  
  
## Note  
 Per impostazione predefinita, lo strumento xdcmake.exe supporta poche opzioni della riga di comando.  Opzioni aggiuntive vengono supportate quando si specifica l'opzione della riga di comando **\/old**.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività **XDCMake**.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Parametro **String\[\]** facoltativo.<br /><br /> Specifica uno o più file .xdc aggiuntivi da unire.<br /><br /> Per ulteriori informazioni, vedere la descrizione **File documenti aggiuntivi** in [Pagina delle proprietà dello strumento generatore di documenti XML](/visual-cpp/ide/xml-document-generator-tool-property-pages).  Vedere anche le opzioni della riga di comando **\/old** e **\/Fs**  per xdcmake.exe.|  
|**AdditionalOptions**|Parametro **String** facoltativo.<br /><br /> Un elenco di opzioni come specificato sulla riga di comando.  Ad esempio, " \/option1 \/option2 \/opzione \#".  Utilizzare questo parametro per specificare opzioni della riga di comando che non sono rappresentate da qualsiasi altro parametro dell'attività **XDCMake**.<br /><br /> Per informazioni dettagliate,  vedere [Riferimento a XDCMake](/visual-cpp/ide/xdcmake-reference), [Pagina delle proprietà dello strumento generatore di documenti XML](/visual-cpp/ide/xml-document-generator-tool-property-pages) e la Guida della riga di comando \(**\/?**\) per xdcmake.exe.|  
|**DocumentLibraryDependencies**|Parametro **Boolean** facoltativo.<br /><br /> Se `true` e il progetto corrente contiene una dipendenza da un progetto di libreria statica \(lib\) all'interno della soluzione, i file xdc per quel progetto di libreria sono inclusi nel file xml di output per il progetto corrente.<br /><br /> Per ulteriori informazioni, vedere la descrizione **Dipendenze libreria documenti** in [Pagina delle proprietà dello strumento generatore di documenti XML](/visual-cpp/ide/xml-document-generator-tool-property-pages).|  
|**OutputFile**|Parametro **String** facoltativo.<br /><br /> Esegue l'override del nome predefinito per i file di output.  Il nome predefinito viene derivato dal nome di base del primo file oggetto xdc che viene elaborato.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/out:**`filename` in [Riferimento a XDCMake](/visual-cpp/ide/xdcmake-reference).  Vedere anche le opzioni della riga di comando **\/old** e **\/Fo**  per xdcmake.exe.|  
|**ProjectName**|Parametro **String** facoltativo.<br /><br /> Nome del progetto corrente.|  
|**SlashOld**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, abilita opzioni xdcmake.exe aggiuntive.<br /><br /> Per ulteriori informazioni, vedere l'opzione della riga di comando **\/old** per xdcmake.exe.|  
|**Sources**|Parametro `ITaskItem[]` obbligatorio.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere utilizzato ed emesso dalle attività.|  
|**SuppressStartupBanner**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del copyright e il messaggio del numero di versione quando l'attività inizia.<br /><br /> Per ulteriori informazioni, vedere l'opzione **\/nologo** in [Riferimento a XDCMake](/visual-cpp/ide/xdcmake-reference).|  
|**TrackerLogDirectory**|Parametro **String** facoltativo.<br /><br /> Specifica la directory per il log dello strumento di rilevamento.|  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)