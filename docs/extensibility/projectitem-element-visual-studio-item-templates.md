---
title: "Elemento ProjectItem (modelli di elementi di Visual Studio) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem> (elemento) [modelli di elemento Visual Studio]"
  - "ProjectItem (elemento) [modelli di elemento Visual Studio]"
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento ProjectItem (modelli di elementi di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica un file che è incluso nel modello di elemento.  
  
> [!NOTE]
>  L'elemento `ProjectItem` accetta diversi attributi in base al modello, se per un progetto o per un elemento.  In questo argomento viene spiegato l'elemento `ProjectItem` per gli elementi.  Per una spiegazione dell'elemento `ProjectItem` per i modelli di progetto, vedere [Elemento ProjectItem \(modelli di progetto Visual Studio\)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
## Sintassi  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## Attributi ed elementi  
 Nelle seguenti sezioni sono illustrati attributi, elementi figlio ed elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`SubType`|Attributo facoltativo.<br /><br /> Specifica il sottotipo di un elemento in un modello di elemento a più file.  Questo valore consente di determinare l'editor che verrà utilizzato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per aprire l'elemento.|  
|`CustomTool`|Attributo facoltativo.<br /><br /> Imposta il CustomTool per l'elemento nel file di progetto.|  
|`ItemType`|Attributo facoltativo.<br /><br /> Imposta l'ItemType per l'elemento nel file di progetto.|  
|`ReplaceParameters`|Attributo facoltativo.<br /><br /> Un valore booleano che specifica se nell'elemento i valori dei parametri dovranno essere sostituiti quando viene creato un progetto dal modello.  Il valore predefinito è `false`.|  
|`TargetFileName`|Attributo facoltativo.<br /><br /> Specifica il nome dell'elemento che viene creato dal modello.  Questo attributo è utile per utilizzare la sostituzione dei parametri per la creazione di un nome di elemento.|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|  
  
## Valore di testo  
 È necessario specificare un valore di testo.  
  
 Una `string` che rappresenta il nome di un file nel file .zip del modello.  
  
## Note  
 `ProjectItem` è un elemento figlio facoltativo di `TemplateContent`.  
  
 L'attributo `TargetFileName` può essere utilizzato per rinominare i file con parametri.  Ad esempio, se nella directory radice del file .zip del modello è presente il file `MyFile.vb`, ma si desidera assegnare al file un nome basato sul nome di file specificato dall'utente nella finestra di dialogo **Aggiungi nuovo elemento**, si dovrà utilizzare il seguente codice XML:  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Quando da questo modello viene creato un elemento, il nome del file sarà basato sul nome specificato dall'utente nella finestra di dialogo **Aggiungi nuovo elemento**.  Ciò è utile quando si creano modelli di elemento a più file.  Per ulteriori informazioni, vedere [Procedura: creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md) e [Parametri di template](../ide/template-parameters.md).  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati i metadati per il modello di elemento standard per una classe di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)   
 [Procedura: creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md)   
 [Parametri di template](../ide/template-parameters.md)