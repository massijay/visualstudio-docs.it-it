---
title: "Elemento SupportsCodeSeparation (modelli di Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation"
helpviewer_keywords: 
  - "<SupportsCodeSeparation> (elemento) [modelli di Visual Studio]"
  - "SupportsCodeSeparation (elemento) [modelli di Visual Studio]"
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Elemento SupportsCodeSeparation (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica se la casella di controllo **Inserisci codice in file separato** verrà abilitata nella finestra di dialogo **Aggiungi nuovo elemento**.  
  
## Sintassi  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce la modalità di visualizzazione per la finestra di dialogo **Nuovo progetto** o **Nuovo elemento**.|  
  
## Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il valore del testo deve essere `true` o `false`, ad indicare se la casella di controllo **Inserisci codice in file separato** verrà abilitata o meno nella finestra di dialogo **Aggiungi nuovo elemento**.  
  
## Note  
 `SupportsCodeSeparation` è un elemento facoltativo.  Il valore predefinito è `false`.  
  
 L'elemento `SupportsCodeSeparation` è disponibile soltanto per i modelli di elemento Web.  
  
 La separazione del codice, o il modello di pagina code\-behind, consente di mantenere il markup in un file e il codice di programmazione in un altro file.  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e altri linguaggi .NET utilizzano questo modello.  
  
## Esempio  
 Nell'esempio riportato di seguito viene specificato di visualizzare l'opzione **Inserisci codice in file separato**.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)