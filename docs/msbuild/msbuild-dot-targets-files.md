---
title: File con estensione targets di MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 17
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
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: e47709e23ae963a9339499eb1b1e1d28834be5bf
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-targets-files"></a>File con estensione targets di MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] include più file con estensione targets che contengono elementi, proprietà, destinazioni e attività per gli scenari comuni. Questi file vengono automaticamente importati nella maggior parte dei file di progetto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per semplificare la manutenzione e la leggibilità.  
  
 I progetti importano generalmente uno o più file con estensione TARGETS per definire il processo di compilazione. Ad esempio, un progetto di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] creato da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] importerà Microsoft.CSharp.targets che importa Microsoft.Common.targets. Il progetto stesso di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] definirà gli elementi e le proprietà specifici di tale progetto, ma le regole di compilazione standard per un progetto di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] vengono definite nei file con estensione targets importati.  
  
 Il valore `$(MSBuildToolsPath)` specifica il percorso di questi file con destinazione .targets comuni. Se `ToolsVersion` è 4.0, i file sono nel percorso seguente: `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
>  Per informazioni su come creare destinazioni personalizzate, vedere [Destinazioni](../msbuild/msbuild-targets.md). Per informazioni su come usare l'elemento `Import` per inserire un file di progetto in un altro file di progetto, vedere [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md) e [Procedura: Usare la stessa destinazione in più file di progetto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  
  
## <a name="common-targets-files"></a>File con estensione targets comuni  
  
|File con estensione targets|Descrizione|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Definisce i passaggi nel processo di compilazione standard per i progetti di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].<br /><br /> Importato dai file Microsoft.CSharp.targets e Microsoft.VisualBasic.targets, che includono l'istruzione seguente: `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Definisce i passaggi nel processo di compilazione standard per i progetti di Visual C#.<br /><br /> Importato dai file di progetto di Visual C# (con estensione csproj), che includono l'istruzione seguente: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Definisce i passaggi nel processo di compilazione standard per i progetti di Visual Basic.<br /><br /> Importato dai file di progetto di Visual Basic (con estensione vbproj), che includono l'istruzione seguente: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
