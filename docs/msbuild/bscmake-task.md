---
title: "Attività BscMake | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 7
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 7522b540558794c702fc5a49972a9e00f785fd2f
ms.lasthandoff: 04/05/2017

---
# <a name="bscmake-task"></a>Attività BscMake
> [!IMPORTANT]
>  Lo strumento bscmake non viene più usato dall'IDE di Visual Studio. A partire da Visual Studio 2008, le informazioni di visualizzazione vengono automaticamente archiviate in un file sdf nella cartella della soluzione.  
  
 Esegue il wrapping dello strumento Microsoft Browse Information Maintenance Utility (bscmake.exe).  Lo strumento bscmake.exe genera un file di informazioni di visualizzazione (con estensione bsc) dai file browser di origine (con estensione sbr) creati durante la compilazione. Usare il **Visualizzatore oggetti** per visualizzare un file con estensione bsc. Per altre informazioni, vedere [Riferimenti a BSCMAKE](/cpp/build/reference/bscmake-reference).  
  
## <a name="parameters"></a>Parametri  
 La tabella seguente illustra i parametri dell'attività **BscMake**. La maggior parte dei parametri attività corrisponde a un'opzione della riga di comando.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**AdditionalOptions**|Parametro **String** facoltativo.<br /><br /> Un elenco di opzioni come specificato sulla riga di comando. Ad esempio, "/*option1* /*option2* /*option#*". Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **BscMake**.<br /><br /> Per altre informazioni, vedere le opzioni in [Opzioni di BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**OutputFile**|Parametro **String** facoltativo.<br /><br /> Specifica un nome di file che esegue l'override del nome del file di output predefinito.<br /><br /> Per altre informazioni, vedere l'opzione **/o** in [Opzioni di BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**PreserveSBR**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, forza una compilazione non incrementale. Viene eseguita una compilazione completa, non incrementale indipendentemente dall'esistenza di un file BSC e impedisce che i file SBR vengano troncati.<br /><br /> Per altre informazioni, vedere l'opzione **/n** in [Opzioni di BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**Sources**|Parametro **ITaskItem[]** facoltativo.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.|  
|**SuppressStartupBanner**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/NOLOGO** in [Opzioni di BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**TrackerLogDirectory**|Parametro **String** facoltativo.<br /><br /> Specifica la directory per il log di Tracker.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)
