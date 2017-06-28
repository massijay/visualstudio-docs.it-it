---
title: 'Procedura: Usare le variabili di ambiente in una compilazione | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 15
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
ms.openlocfilehash: 352950f52c335be52b1765a6008c26db1550a5b0
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-use-environment-variables-in-a-build"></a>Procedura: utilizzare le variabili di ambiente in una compilazione
Quando si compilano i progetti, spesso è necessario impostare le opzioni di compilazione usando informazioni non incluse nel file di progetto o nei file che costituiscono il progetto. Queste informazioni sono in genere archiviate nelle variabili di ambiente.  
  
## <a name="referencing-environment-variables"></a>Riferimento alle variabili di ambiente  
 Tutte le variabili di ambiente sono disponibili per il file di progetto [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) come proprietà.  
  
> [!NOTE]
>  Se il file di progetto contiene una definizione esplicita di una proprietà con lo stesso nome di una variabile di ambiente, la proprietà nel file di progetto esegue l'override del valore della variabile di ambiente.  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Per usare una variabile di ambiente in un progetto MSBuild  
  
-   Fare riferimento alla variabile di ambiente esattamente come a una variabile dichiarata nel file di progetto. Il codice seguente, ad esempio, fa riferimento alla variabile di ambiente BIN_PATH:  
  
     `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
 È possibile usare un attributo `Condition` per fornire un valore predefinito per una proprietà se la variabile di ambiente non è stata impostata.  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>Per fornire un valore predefinito per una proprietà  
  
-   Usare un attributo `Condition` in una proprietà per impostare il valore solo se la proprietà non ha un valore. Il codice seguente, ad esempio, imposta la proprietà `ToolsPath` su c:\tools solo se la variabile di ambiente `ToolsPath` non è impostata:  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    >  Per i nomi delle proprietà non viene rilevata la distinzione tra maiuscole e minuscole, quindi sia `$(ToolsPath)` che `$(TOOLSPATH)` fanno riferimento alla stessa proprietà o variabile di ambiente.  
  
## <a name="example"></a>Esempio  
 Il file di progetto seguente usa variabili di ambiente per specificare il percorso delle directory.  
  
```xml  
<Project DefaultTargets="FakeBuild">  
    <PropertyGroup>  
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>  
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">  
            C:\Tools  
        </ToolsPath>  
    </PropertyGroup>  
    <Target Name="FakeBuild">  
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
    [MSBuild ](../msbuild/msbuild.md)
    [MSBuild Properties](../msbuild/msbuild-properties.md)
 [Procedura: Compilare gli stessi file di origine con opzioni diverse](../msbuild/how-to-build-the-same-source-files-with-different-options.md)