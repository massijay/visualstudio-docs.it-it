---
title: "Elemento ProjectTemplateLink (modelli di Visual Studio) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink"
helpviewer_keywords: 
  - "<ProjectTemplateLink> (elemento) [modelli di Visual Studio]"
  - "ProjectTemplateLink (elemento) [modelli di Visual Studio]"
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento ProjectTemplateLink (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica il percorso del file .vstemplate di un progetto in un modello multiprogetto.  
  
## Sintassi  
  
```  
<ProjectTemplateLink ProjectName="Name">     PathToTemplateFile </ProjectTemplateLink>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`ProjectName`|Attributo facoltativo.<br /><br /> Specifica il nome di ogni singolo progetto in un modello multiprogetto.  Nella finestra di dialogo **Nuovo progetto** non è possibile assegnare nomi a progetti singoli.|  
|`CopyParameters`|Consente la copia di tutte le variabili nel modello del gruppo centrale in ognuno dei modelli collegati.<br /><br /> I parametri nei modelli collegati dispongono del prefisso `"$ext_*$"`.  Ad esempio, se nel modello del gruppo padre il parametro `$projectname$` contiene un valore ExampleProject1, il modello collegato nel momento in cui deve essere eseguito acquisisce un parametro `$ext_projectname$`, che è una copia del parametro `$projectname$` dal modello del gruppo padre.<br /><br /> In questo modo i modelli collegati possono condividere alcuni parametri comuni, che possono essere facilmente creati solo nel modello del gruppo padre.<br /><br /> Questo attributo è facoltativo ed è automaticamente impostato su `false` quando non è incluso.<br /><br /> Introdotto in Visual Studio 2013 Update 2.  Per fare riferimento alla versione di prodotto corretta, vedere [Referencing Assemblies Delivered in the Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/it-it/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Specifica l'organizzazione e i contenuti dei modelli multiprogetto.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Raggruppa i progetti in modelli multiprogetto.|  
  
## Valore di testo  
 È necessario specificare un valore di testo.  
  
 Questo testo specifica il percorso del file .vstemplate del modello.  
  
## Note  
 I modelli multiprogetto fungono da contenitori per due o più progetti.  L'elemento `ProjectTemplateLink` viene utilizzato per specificare il percorso del file .vstemplate per uno dei progetti presenti nel modello.  Il file .vstemplate di un modello multiprogetto contiene un elemento `ProjectTemplateLink` per ciascun progetto presente nel modello.  Per altre informazioni sui modelli multiprogetto, vedere [Procedura: creare modelli basati su più progetti](../ide/how-to-create-multi-project-templates.md).  
  
## Esempio  
 Nell'esempio riportato di seguito viene mostrato un file .vstemplate radice multiprogetto semplice.  In questo esempio, il modello contiene due progetti `My Windows Application` e `My Class Library`.  L'attributo `ProjectName` nell'elemento `ProjectTemplateLink` imposta il nome per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da assegnare a questo progetto.  Se l'attributo `ProjectName` non esiste, per il nome del progetto verrà utilizzato il nome del file .vstemplate.  
  
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
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)   
 [Procedura: creare modelli basati su più progetti](../ide/how-to-create-multi-project-templates.md)