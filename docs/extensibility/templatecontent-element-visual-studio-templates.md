---
title: "Elemento TemplateContent (modelli di Visual Studio) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent"
helpviewer_keywords: 
  - "TemplateContent (elemento) [modelli di progetto Visual Studio]"
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento TemplateContent (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica il contenuto del modello.  
  
## Sintassi  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|Specifica se compilare la soluzione quando viene creato un progetto dal modello.|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica l'organizzazione e i contenuti dei modelli multiprogetto.|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica i file o le directory da aggiungere al progetto.|  
|[Riferimenti](../extensibility/references-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica i riferimenti agli assembly necessari per un modello di elemento.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Elemento facoltativo.<br /><br /> Specifica un file contenuto nel modello.|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica tutti i parametri personalizzati che devono essere utilizzati quando un progetto o un elemento dal modello.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Contiene tutti i metadati per il modello di progetto, il modello di elemento o lo starter kit.|  
  
## Note  
 `TemplateContent` è un elemento obbligatorio.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati i metadati per un modello di progetto di un'applicazione di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
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