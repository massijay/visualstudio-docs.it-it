---
title: "Procedura: creare manualmente modelli Web | Microsoft Docs"
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
  - "modelli di progetto [Visual Studio], Web"
  - "modelli [Visual Studio], Web"
  - "modelli di Visual Studio, Web"
  - "modelli Web [Visual Studio]"
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: creare manualmente modelli Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La creazione di un modello Web è leggermente diversa dalla creazione di altri tipi di modello.  Poiché i modelli di progetto Web vengono visualizzati nella finestra di dialogo **Aggiungi nuovo sito Web** e gli elementi dei progetti Web vengono classificati in base al linguaggio di programmazione, è necessario specificare nel file con estensione vstemplate il modello come modello Web e identificare il linguaggio di programmazione.  
  
> [!NOTE]
>  I modelli Web devono contenere un file con estensione webproj vuoto specificato utilizzando l'attributo `File` dell'elemento `Project`.  Anche se i progetti Web non necessitano di file di progetto, questo file è necessario per il corretto funzionamento dei modelli Web.  
  
### Per creare manualmente un modello Web  
  
1.  Creare un progetto Web.  
  
2.  Modificare o eliminare i file nel progetto o aggiungere nuovi file al progetto.  
  
3.  Creare un nuovo file XML e salvarlo con estensione vstemplate nella stessa directory del progetto.  Non aggiungerlo al progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Creare il file XML .vstemplate per fornire i metadati del modello di progetto.  Per ulteriori informazioni, vedere l'esempio nella sezione seguente.  
  
5.  Individuare l'elemento `ProjectType` nel file .vstemplate e impostare il valore del testo su `Web`.  
  
6.  Seguendo l'elemento `ProjectType`, aggiungere un elemento `ProjectSubType` e impostare il valore del testo sul linguaggio di programmazione del modello.  Il linguaggio di programmazione può assumere uno dei valori seguenti:  
  
    -   CSharp  
  
    -   VisualBasic  
  
     Di seguito è riportato un esempio:  
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  Selezionare i file inclusi nel modello \(incluso il file con estensione vstemplate\), fare clic con il pulsante destro del mouse sulla selezione, scegliere **Invia a**, quindi fare clic su **Cartella compressa**.  I file verranno compressi in un file .zip.  
  
8.  Inserire il file con estensione zip del modello nella directory del modello di progetto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  per impostazione predefinita, questa directory è \\My Documents\\Visual Studio *versione*\\My Exported Templates \\.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un file semplice con estensione vstemplate per un modello di progetto Web.  
  
```  
<VSTemplate Version="2.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
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
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)