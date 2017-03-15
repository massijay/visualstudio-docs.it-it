---
title: "Elemento ProjectItem (modelli di progetto Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem> (elemento) [modelli di progetto Visual Studio]"
  - "ProjectItem (elemento) [modelli di progetto Visual Studio]"
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Elemento ProjectItem (modelli di progetto Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica un file che è incluso nel modello di progetto.  
  
> [!NOTE]
>  L'elemento `ProjectItem` accetta diversi attributi in base al modello, se per un progetto o per un elemento.  In questo argomento viene spiegato l'elemento `ProjectItem` per i modelli di progetto.  Per una spiegazione dell'elemento `ProjectItem` per i modelli di elemento, vedere [Elemento ProjectItem \(modelli di elementi di Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
## Sintassi  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## Attributi ed elementi  
 Nelle seguenti sezioni sono illustrati attributi, elementi figlio ed elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`TargetFileName`|Attributo facoltativo.<br /><br /> Specifica il nome e il percorso dell'elemento di progetto quando viene creato un progetto dal modello.  Questo attributo è utile per creare una struttura di directory diversa dalla struttura di directory presente nel file .zip del modello o per utilizzare la sostituzione dei parametri per la creazione di un nome di elemento.|  
|`ReplaceParameters`|Attributo facoltativo.<br /><br /> Un valore booleano che specifica se nell'elemento i valori dei parametri dovranno essere sostituiti quando viene creato un progetto dal modello.  Il valore predefinito è `false`.|  
|`OpenInEditor`|Attributo facoltativo.<br /><br /> Un valore booleano che specifica se l'elemento dovrà essere aperto nel rispettivo editor in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] quando viene creato un progetto dal modello.<br /><br /> Gli attributi `OpenInWebBrowser` e `OpenInHelpBrowser` vengono ignorati in un elemento con un valore `OpenInEditor` impostato su `true`.<br /><br /> Il valore predefinito è `false`.|  
|`OpenInWebBrowser`|Attributo facoltativo.<br /><br /> Un valore booleano che specifica se l'elemento dovrà essere aperto nel browser Web quando viene creato un progetto dal modello.<br /><br /> Nel browser Web è possibile aprire solo i file HTML e i file di testo locali del progetto.  Gli URL esterni non possono essere aperti con questo attributo.<br /><br /> Il valore predefinito è `false`.|  
|`OpenInHelpBrowser`|Attributo facoltativo.<br /><br /> Un valore booleano che specifica se l'elemento dovrà essere aperto nel visualizzatore della Guida quando viene creato un progetto dal modello.<br /><br /> Nel browser della Guida è possibile aprire solo i file HTML e i file di testo locali del progetto.  Gli URL esterni non possono essere aperti con questo attributo.<br /><br /> Il valore predefinito è `false`.|  
|`OpenOrder`|Attributo facoltativo.<br /><br /> Specifica un valore numerico che rappresenta l'ordine in cui gli elementi verranno aperti nei rispettivi editor.  Tutti i valori devono essere multipli di 10.  Gli elementi con i valori maggiori `OpenOrder` vengono aperti prima.|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Specifica i file o le directory da aggiungere al progetto.|  
  
## Valore di testo  
 È necessario specificare un valore di testo.  
  
 Una `string` che rappresenta il nome o il percorso di un file nel file .zip del modello.  
  
## Note  
 `ProjectItem` è un elemento figlio facoltativo di `Project`.  
  
 È possibile utilizzare l'attributo `TargetFileName` per creare una struttura di directory diversa dalla struttura di directory presente nel file .zip del modello.  Ad esempio, se nella directory radice del file .zip del modello è presente il file `MyFile.vb`, ma si desidera inserire questo file in una directory denominata `CustomFiles` in tutti i progetti creati dal modello, si dovrà utilizzare il seguente codice XML:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 L'attributo `TargetFileName` può essere utilizzato anche per rinominare file i cui nomi contengpono caratteri internazionali.  Ad esempio, il file zip di un modello non può contenere nomi di file con caratteri Unicode, pertanto è necessario rinominarli prima di comprimerli in un file zip.  L'attributo `TargetFileName` può essere utilizzato per reimpostare il nome del file sul nome Unicode originale.  
  
 L'attributo `TargetFileName` può essere utilizzato anche per rinominare i file con parametri.  La procedura descritta di seguito illustra come rinominare il file `MyFile.vb` presente nella directory radice del file zip del modello utilizzando un nome file basato sul nome del progetto.  
  
### Per rinominare i file con parametri  
  
1.  Utilizzare il codice XML seguente nel file vstemplate:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  Aprire il file del progetto \(con estensione vbproj per un progetto [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) in un editor di testo o in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Nel file del progetto individuare la riga analoga al seguente codice XML:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  Sostituire le riga di codice con il seguente codice XML:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Quando da questo modello viene creato un progetto, il nome del file sarà basato sul nome specificato dall'utente nella finestra di dialogo **Nuovo progetto**, dal quale sono stati rimossi i caratteri non sicuri e gli spazi.  Per ulteriori informazioni, vedere [Parametri di template](../ide/template-parameters.md).  
  
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
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
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
 [Parametri di template](../ide/template-parameters.md)   
 [Elemento ProjectItem \(modelli di elementi di Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md)