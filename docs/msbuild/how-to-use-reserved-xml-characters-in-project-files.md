---
title: "Procedura: utilizzare caratteri XML riservati nei file di progetto | Microsoft Docs"
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
  - "MSBuild, utilizzo di caratteri XML riservati"
  - "MSBuild, i caratteri XML riservati"
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: utilizzare caratteri XML riservati nei file di progetto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si creano file di progetto, potrebbe essere necessario utilizzare caratteri XML riservati, ad esempio, i valori delle proprietà o dei parametri delle attività. Tuttavia, alcuni caratteri riservati devono essere sostituiti da un'entità denominata in modo che il file di progetto può essere analizzato.  
  
## <a name="using-reserved-characters"></a>Utilizzo di caratteri riservati  
 Nella tabella seguente vengono descritti i caratteri XML riservati che devono essere sostituiti da entità denominata corrispondente in modo che il file di progetto può essere analizzato.  
  
|Carattere riservato|Entità denominata|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Usare le virgolette doppie in un file di progetto  
  
-   Sostituire le virgolette doppie con i corrispondenti entità, denominata &quot;. Ad esempio, per utilizzare le virgolette doppie intorno il `EXEFile` elemento elenco, digitare:  
  
    ```  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente, le virgolette doppie vengono utilizzate per evidenziare il nome del file nel messaggio di output dal file di progetto.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is "@(EXEFile)"."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti di MSBuild](../msbuild/msbuild-reference.md)
 [MSBuild](../msbuild/msbuild1.md)