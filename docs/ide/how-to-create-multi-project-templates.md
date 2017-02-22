---
title: "Procedura: creare modelli basati su pi&#249; progetti | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelli multiprogetto"
  - "modelli di progetto, creazione di modelli multiprogetto"
  - "modelli di Visual Studio, creazione di modelli multiprogetto"
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: creare modelli basati su pi&#249; progetti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I modelli multiprogetto fungono da contenitori per due o più progetti.  Quando nella finestra di dialogo **Nuovo progetto** viene creato un progetto basato su un modello multiprogetto, ogni progetto nel modello viene aggiunto alla soluzione.  
  
 Un modello multiprogetto deve contenere gli elementi riportati di seguito, compressi in un file con estensione zip:  
  
-   Un file .vstemplate radice per l'intero modello multiprogetto.  Il file radice con estensione vstemplate contiene i metadati che verranno visualizzati nella finestra di dialogo **Nuovo progetto** e specifica l'ubicazione dei file dei progetti in questo modello.  Questo file deve risiedere nella directory radice del file .zip.  
  
-   Una o più cartelle contenenti i file necessari per un modello di progetto completo,  tra cui tutti i file di codice e un file con estensione vstemplate relativi al progetto.  
  
 Ad esempio, un file con estensione zip di un modello multiprogetto con due progetti potrebbe includere i file e le directory seguenti:  
  
 MultiProjectTemplate.vstemplate  
  
 \\Project1\\Project1.vstemplate  
  
 \\Project1\\Project1.vbproj  
  
 \\Project1\\Class.vb  
  
 \\Project2\\Project2.vstemplate  
  
 \\Project2\\Project2.vbproj  
  
 \\Project2\\Class.vb  
  
 Il file radice con estensione vstemplate radice per un modello multiprogetto differisce da un modello a progetto singolo nelle seguenti caratteristiche:  
  
-   L'attributo `Type` dell'elemento `VSTemplate` contiene il valore `ProjectGroup`.  Di seguito è riportato un esempio:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="ProjectGroup"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    ```  
  
-   L'elemento `TemplateContent` contiene un elemento `ProjectCollection` con uno o più elementi `ProjectTemplateLink` che definiscono i percorsi dei file con estensione vstemplate dei progetti inclusi.  Di seguito è riportato un esempio:  
  
    ```  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink>  
                Project1\Project1.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink>  
                Project2\Project2.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
    ```  
  
 Inoltre, i modelli multiprogetto si comportano diversamente dai modelli normali.  I modelli multiprogetto presentano le seguenti caratteristiche univoche:  
  
-   Ai singoli modelli di un modello multiprogetto non è possibile assegnare i nomi tramite la finestra di dialogo **Nuovo progetto**.  Per specificare il nome di ogni progetto è necessario invece utilizzare l'attributo `ProjectName` nell'elemento `ProjectTemplateLink`.  Per ulteriori informazioni, vedere il primo esempio nella sezione di seguito.  
  
-   I modelli multiprogetto possono contenere progetti scritti in linguaggi diversi, ma l'intero modello può essere inserito in un'unica categoria utilizzando l'elemento `ProjectType`.  
  
### Per creare un modello multiprogetto  
  
1.  Creare i progetti da includere nel modello multiprogetto.  
  
2.  Creare i file con estensione vstemplate per ogni progetto.  Per ulteriori informazioni, vedere [Procedura: creare modelli di progetto](../ide/how-to-create-project-templates.md).  
  
3.  Creare un file radice con estensione vstemplate che includerà i metadati per il modello multiprogetto.  Per ulteriori informazioni, vedere il primo esempio nella sezione di seguito.  
  
4.  Selezionare i file e le cartelle da includere nel modello, fare clic con il pulsante destro del mouse sulla selezione, scegliere **Invia a**, quindi fare clic su **Cartella compressa**.  I file e le cartelle verranno compressi in un file .zip.  
  
5.  Inserire il file con estensione zip del modello nella directory del modello di progetto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  per impostazione predefinita, questa directory è \\My Documents\\Visual Studio *versione*\\Templates\\ProjectTemplates \\.  
  
## Esempio  
 Nell'esempio riportato di seguito viene mostrato un file radice con estensione vstemplate multiprogetto di base.  In questo esempio, il modello contiene due progetti `My Windows Application` e `My Class Library`.  L'attributo `ProjectName` nell'elemento `ProjectTemplateLink` imposta il nome per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da assegnare a questo progetto.  Se l'attributo `ProjectName` non esiste, per il nome del progetto verrà utilizzato il nome del file .vstemplate.  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
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
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Esempio  
 Nell'esempio riportato di seguito, l'elemento `SolutionFolder` viene utilizzato per dividere i progetti in due gruppi, `Math Classes` e `Graphics Classes`.  Il modello contiene quattro progetti, due dei quali vengono inseriti in ogni cartella della soluzione.  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
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
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Procedura: creare modelli di progetto](../ide/how-to-create-project-templates.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Elemento SolutionFolder \(modelli di Visual Studio\)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [Elemento ProjectTemplateLink \(modelli di Visual Studio\)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)