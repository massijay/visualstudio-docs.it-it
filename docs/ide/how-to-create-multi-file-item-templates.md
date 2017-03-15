---
title: "Procedura: creare modelli di elementi a pi&#249; file | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelli di elementi, creazione di modelli di elementi a più file"
  - "modelli di elementi a più file"
  - "modelli di Visual Studio, creazione di modelli di elementi a più file"
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Procedura: creare modelli di elementi a pi&#249; file
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I modelli di elemento possono specificare un solo elemento, ma talvolta l'elemento è composto da più file.  Ad esempio, un modello di elemento Windows Form per Visual Basic richiede i tre file seguenti:  
  
-   Un file .vb che contiene il codice per il form.  
  
-   Un file designer.vb che contiene le informazioni di progettazione per il form.  
  
-   Un file resx.vb che contiene le risorse incorporate per il form.  
  
 Nei modelli di elemento a più file è necessario utilizzare alcuni parametri per garantire che verranno adottate le estensioni di file corrette quando l'elemento verrà creato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Se il modello di elemento viene creato tramite l'**Esportazione guidata modelli**, questi parametri vengono generati automaticamente e non sono necessarie ulteriori operazioni di modifica.  Nella procedura riportata di seguito viene illustrato come utilizzare i parametri per garantire la creazione delle estensioni di file corrette.  
  
### Per creare manualmente un modello di elemento a più file  
  
1.  Creare il modello di elemento seguendo la stessa procedura per la creazione di un modello di elemento con un unico file.  Per ulteriori informazioni, vedere [Procedura: creare modelli di elementi](../ide/how-to-create-item-templates.md).  
  
2.  Aggiungere gli attributi `TargetFileName` a ogni elemento `ProjectItem`.  Impostare i valori degli attributi `TargetFileName` su $fileinputname$.*FileExtension*, dove *FileExtension* è l'estensione del file che verrà incluso nel modello.  Di seguito è riportato un esempio:  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     Quando a un progetto viene aggiunto un elemento derivato da questo modello, i nomi dei file verranno creati in base al nome specificato dall'utente nella finestra di dialogo **Aggiungi nuovo elemento**.  
  
3.  Selezionare i file da includere nel modello, fare clic con il pulsante destro del mouse sulla selezione, scegliere **Invia a**, quindi fare clic su **Cartella compressa**.  I file selezionati verranno compressi in un file .zip.  
  
4.  Inserire il file con estensione zip nel percorso dei modelli di elemento dell'utente.  Per impostazione predefinita, è \\My Documents\\Visual Studio *versione*\\Templates\\ItemTemplates \\.  Per ulteriori informazioni, vedere [Procedura: individuare e organizzare modelli](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## Esempio  
 Nell'esempio riportato di seguito viene mostrato un modello di Windows Form di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Quando viene creato un elemento basato su questo modello, i nomi dei tre file creati corrisponderanno ai nomi specificati nella finestra di dialogo **Aggiungi nuovo elemento**.  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Vedere anche  
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)   
 [Procedura: creare modelli di elementi](../ide/how-to-create-item-templates.md)   
 [Parametri di template](../ide/template-parameters.md)   
 [Procedura: sostituire i parametri di un modello](../ide/how-to-substitute-parameters-in-a-template.md)