---
title: "CreateInPlace (modelli di Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace"
helpviewer_keywords: 
  - "<CreateInPlace> (elemento) [modelli di Visual Studio]"
  - "CreateInPlace (elemento) [modelli di Visual Studio]"
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# CreateInPlace (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica se creare il progetto ed eseguire la sostituzione dei parametri nella posizione specificata oppure se eseguire la sostituzione dei parametri in una posizione temporanea e quindi salvare il progetto nella posizione specificata.  
  
## Sintassi  
  
```  
<CreateInPlace> true/false </CreateInPlace>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
 Nessuno.  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello e definisce la modalità di visualizzazione per la finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento**.|  
  
## Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo deve essere `true` o `false`.  Se è `true`, il progetto viene creato e la sostituzione dei parametri viene eseguita nella posizione specificata nella finestra di dialogo **Nuovo progetto**.  Se è `false`, la sostituzione dei parametri viene eseguita in una posizione temporanea e il progetto verrà poi copiato nella posizione specificata.  
  
## Note  
 `CreateInPlace` è un elemento facoltativo.  Il valore predefinito è `true`.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati i metadati per un modello di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <CreateInPlace>false</CreateInPlace>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Vedere anche  
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)