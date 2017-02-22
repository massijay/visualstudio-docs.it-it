---
title: "Elemento ProjectSubType (modelli di Visual Studio) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType"
helpviewer_keywords: 
  - "<ProjectSubType> (elemento) [modelli di Visual Studio]"
  - "ProjectSubType (elemento) [modelli di Visual Studio]"
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento ProjectSubType (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Classifica il modello in una sottocategoria del valore specificato nell'elemento `ProjectType`.  
  
## Sintassi  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## Attributi ed elementi  
 Nelle seguenti sezioni sono illustrati attributi, elementi figlio ed elementi padre.  
  
### Attributi  
 Nessuno.  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce la modalità di visualizzazione per la finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento**.|  
  
## Valore di testo  
 È necessario specificare un valore di testo.  
  
 Questo valore definisce la sottocategoria del modello.  
  
## Note  
 `ProjectSubType` è un elemento figlio facoltativo di `TemplateData`.  
  
 L'elemento `ProjectSubType` fornisce una sottocategoria dell'elemento [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md).  Questo valore può includere:  
  
-   `SmartDevice-NETCFv1`: specifica che il modello è destinato a [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versione 1.0.  
  
-   `SmartDevice-NETCFv2`: specifica che il modello è destinato a [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versione 2.0.  
  
 Se il modello contiene un elemento `ProjectType` con un valore di `Web`, l'elemento `ProjectSubType` specifica il linguaggio di programmazione del modello.  Per l'elemento è possibile specificare i seguenti valori:  
  
-   `CSharp`: specifica che dal modello verrà creato un progetto o un elemento Web di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
-   `VisualBasic`: specifica che dal modello verrà creato un progetto o un elemento Web di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati i metadati di un modello di progetto per un'applicazione per dispositivi di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] destinata a [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versione 2.0.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
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
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)   
 [Elemento ProjectType \(modelli di Visual Studio\)](../extensibility/projecttype-element-visual-studio-templates.md)