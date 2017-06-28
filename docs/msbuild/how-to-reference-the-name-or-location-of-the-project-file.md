---
title: 'Procedura: Fare riferimento al nome o al percorso del file di progetto | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 13
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
ms.openlocfilehash: cd4ed0d5d7df332bd1f49edd5989f56a09293c44
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Procedura: fare riferimento al nome o al percorso del file di progetto
È possibile usare il nome o il percorso del progetto nel file di progetto senza dover creare una proprietà. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornisce proprietà riservate che fanno riferimento al nome file di progetto e altre proprietà relative al progetto. Per altre informazioni sulle proprietà riservate, vedere [Proprietà riservate e note di MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Uso della proprietà MSBuildProjectName  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornisce alcune proprietà riservate che è possibile usare nei file di progetto senza definirle ogni volta. La proprietà riservata `MSBuildProjectName`, ad esempio, fornisce un riferimento al nome file di progetto.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>Per usare la proprietà MSBuildProjectName  
  
-   Fare riferimento alla proprietà nel file di progetto con la notazione $(), come per qualsiasi altra proprietà. Ad esempio:  
  
    ```xml  
    <CSC Sources = "@(CSFile)"   
        OutputAssembly = "$(MSBuildProjectName).exe"/>  
    </CSC>  
    ```  
  
 Uno dei vantaggi dell'uso di una proprietà riservata è che eventuali modifiche apportate al nome file di progetto vengono incorporate automaticamente. La volta successiva in cui si compila il progetto, il file di output assumerà il nuovo nome senza nessuna altra azione da parte dell'utente.  
  
> [!NOTE]
>  Le proprietà riservate non possono essere ridefinite nel file di progetto.  
  
## <a name="example"></a>Esempio  
 Il file di progetto di esempio seguente fa riferimento al nome del progetto come proprietà riservata per specificare il nome per l'output.  
  
```xml  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
[MSBuild](../msbuild/msbuild.md)  
 [Proprietà riservate e note MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)