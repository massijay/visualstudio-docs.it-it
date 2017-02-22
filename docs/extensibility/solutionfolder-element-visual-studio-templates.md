---
title: "Elemento SolutionFolder (modelli di Visual Studio) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder"
helpviewer_keywords: 
  - "<SolutionFolder> (elemento) [modelli di Visual Studio]"
  - "SolutionFolder (elemento) [modelli di Visual Studio]"
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento SolutionFolder (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Raggruppa i progetti in modelli multiprogetto.  
  
## Sintassi  
  
```  
<SolutionFolder Name="DirectoryName">  
    ...  
</SolutionFolder>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Attributo obbligatorio.<br /><br /> Nome della cartella della soluzione.|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica il percorso del file .vstemplate di un progetto in un modello multiprogetto.|  
|`SolutionFolder`|Elemento facoltativo.<br /><br /> Raggruppa i progetti in modelli multiprogetto.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Specifica l'organizzazione e i contenuti dei modelli multiprogetto.|  
|`SolutionFolder`|Raggruppa i progetti in modelli multiprogetto.|  
  
## Note  
 I modelli multiprogetto fungono da contenitori per due o più progetti.  L'elemento `SolutionFolder` viene usato per organizzare i progetti in gruppi all'interno del modello.  Le cartelle specificate dagli elementi `SolutionFolder` vengono create come cartelle della soluzione nel progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Per ulteriori informazioni sui modelli multiprogetto, vedere [Procedura: creare modelli basati su più progetti](../ide/how-to-create-multi-project-templates.md).  
  
## Esempio  
 Questo esempio usa l'elemento `SolutionFolder` per dividere il modello multiprogetto in due gruppi, `Math Classes` e `Graphics Classes`.  Il modello contiene quattro progetti, due dei quali vengono inseriti in ogni cartella della soluzione.  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)   
 [Procedura: creare modelli basati su più progetti](../ide/how-to-create-multi-project-templates.md)