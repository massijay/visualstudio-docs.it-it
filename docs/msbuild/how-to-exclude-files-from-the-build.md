---
title: "Procedura: escludere file dalla compilazione | Microsoft Docs"
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
  - "MSBuild, i caratteri jolly"
  - "MSBuild, esclusione di file"
  - "caratteri jolly, MSBuild"
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: escludere file dalla compilazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In un file di progetto è possibile utilizzare caratteri jolly per includere tutti i file in una directory o un gruppo nidificato di directory come input per una compilazione. Tuttavia, potrebbe essere presente un file nella directory o una directory in un insieme annidato di directory che non si desidera includere come input per una compilazione. È possibile escludere in modo esplicito il file o directory dall'elenco di input. Potrebbe inoltre essere presente un file in un progetto che si desidera includere in determinate condizioni. È possibile dichiarare in modo esplicito le condizioni in cui è incluso un file in una compilazione.  
  
## <a name="excluding-a-file-or-directory-from-the-inputs-for-a-build"></a>Esclusione di un File o Directory dagli input per una compilazione  
 Elemento gli elenchi sono i file di input per una compilazione. Gli elementi che si desiderano includere vengono dichiarati separatamente o come un gruppo utilizzando il `Include` attributo. Ad esempio:  
  
```  
<CSFile Include="Form1.cs"/>  
<CSFile Include ="File1.cs;File2.cs"/>  
<CSFile Include="*.cs"/>  
<JPGFile Include="Images\**\*.jpg"/>  
```  
  
 Se si utilizzano caratteri jolly per includere tutti i file in una directory o un gruppo nidificato di directory come input per una compilazione, potrebbero essere presenti uno o più file nella directory o una delle directory di un gruppo nidificato di directory che non si desidera includere. Per escludere un elemento dall'elenco di elementi, utilizzare il `Exclude` attributo.  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Per includere tutti i file con estensione cs o vb, ad eccezione di Form2  
  
-   Utilizzare uno dei seguenti `Include` e `Exclude` attributi:  
  
    ```  
    <CSFile Include="*.cs" Exclude="Form2.cs"/>  
    ```  
  
     - oppure -  
  
    ```  
    <VBFile Include="*.vb" Exclude="Form2.vb"/>  
    ```  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Per includere tutti i file con estensione cs o vb eccetto Form2 e Form3  
  
-   Utilizzare uno dei seguenti `Include` e `Exclude` attributi:  
  
    ```  
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>  
    ```  
  
     - oppure -  
  
    ```  
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>  
    ```  
  
#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Per includere tutti i file. jpg nella sottodirectory della directory Images, ad eccezione di quelli della directory Version2  
  
-   Utilizzare la seguente `Include` e `Exclude` attributi:  
  
    ```  
    <JPGFile  
        Include="Images\**\*.jpg"  
        Exclude = "Images\**\Version2\*.jpg"/>  
    ```  
  
    > [!NOTE]
    >  È necessario specificare il percorso per entrambi gli attributi. Se si utilizza un percorso assoluto per specificare percorsi di file nel `Include` attributo, è inoltre necessario utilizzare un percorso assoluto nel `Exclude` attributo; se si utilizza un percorso relativo nel `Include` attributo, è inoltre necessario utilizzare un percorso relativo nel `Exclude` attributo.  
  
## <a name="using-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Utilizzo di condizioni per escludere un File o Directory dagli input per una compilazione  
 Se sono presenti elementi che si desiderano includere, ad esempio, in una build di Debug ma non una build di rilascio, è possibile utilizzare il `Condition` attributo per specificare le condizioni in cui includere l'elemento.  
  
#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Per includere il file formula. vb solo nelle build di rilascio  
  
-   Utilizzare un `Condition` attributo simile al seguente:  
  
    ```  
    <Compile  
        Include="Formula.vb"  
        Condition=" '$(Configuration)' == 'Release' " />  
    ```  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente compila un progetto con tutti i file con estensione cs nella directory tranne Form2.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs Exclude="Form2.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi](../msbuild/msbuild-items.md)   
 [MSBuild](../msbuild/msbuild1.md)
 [procedura: selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md)