---
title: 'Procedura: Creare modelli di elementi | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ecd17694e65c6273f8e73a321a72bc209038922
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-item-templates"></a>Procedura: creare modelli di elementi
I passaggi inclusi nella [prima procedura](../ide/how-to-create-item-templates.md#export_template) di questo argomento illustrano come creare un modello di elemento usando l'**Esportazione guidata modelli**. Se il modello è costituito da più file, vedere [Procedura: Creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md).  

 La procedura guidata esegue automaticamente molte operazioni per la creazione del modello di base, ma in molti casi sarà necessario modificare manualmente il file con estensione vstemplate dopo aver esportato il modello. Ad esempio, se si vuole includere l'elemento nella finestra di dialogo**Aggiungi nuovo elemento** per un progetto app di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], è necessario eseguire alcuni passaggi aggiuntivi. La [seconda procedura](../ide/how-to-create-item-templates.md#modify_template) di questo argomento illustra come eseguire tale operazione.  

 Per specificare che il modello deve essere visualizzato solo per determinati sottotipi di progetto, ad esempio Office, Database o Web, vedere [questa sezione](#enable_templates).  

 In alcuni casi può essere utile o necessario creare manualmente un modello di elemento da zero. La [terza procedura](../ide/how-to-create-item-templates.md#create_template) illustra come eseguire tale operazione.  

 Per informazioni sugli elementi che è possibile usare nel file con estensione vstemplate, vedere [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  

### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>Per aggiungere un modello di elemento del progetto personalizzato alla finestra di dialogo Aggiungi nuovo elemento  

1.  Creare o aprire un progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  

2.  Aggiungere un elemento al progetto e, se si desidera, modificarlo.  

3.  Modificare il file del codice per indicare dove verrà applicata la sostituzione dei parametri. Per altre informazioni, vedere [Procedura: Sostituire i parametri di un modello](../ide/how-to-substitute-parameters-in-a-template.md).  

4.  Nel menu **Progetto** scegliere**Esporta modello**.  

5.  Scegliere **Modello di elemento**, selezionare il progetto che contiene l'elemento e quindi fare clic su **Avanti**.  

6.  Selezionare l'elemento per il quale creare il modello e fare clic su **Avanti**.  

7.  Selezionare i riferimenti all'assembly da includere nel modello e fare clic su **Avanti**.  

8.  Digitare il nome del file icona, l'immagine di anteprima, il nome del modello e la descrizione del modello e fare clic su **Fine**.  

     I file per il modello vengono aggiunti a un file ZIP e copiati nella directory specificata nella finestra di dialogo. Il percorso predefinito è la cartella **..\Utenti\\<nomeutente\>\Documenti\Visual Studio \<versione>\My Exported Templates\\**.  

    > [!WARNING]
    >  Nelle versioni precedenti di Visual Studio, il percorso predefinito è **..Utenti\\<nomeutente\>\Documenti\Visual Studio \<versione>\Templates\ItemTemplates**.  

### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>Per abilitare l'uso del modello di elemento in un progetto Windows Store  

1.  Seguire i passaggi nella procedura precedente per esportare un modello di elemento.  

2.  Estrarre il file con estensione vstemplate dal file ZIP che è stato copiato nella cartella ..Utenti\\*nomeutenti*\Documenti\Visual Studio *versione*\Templates\ItemTemplates\ (o **My Exported Templates**).  

3.  Aprire il file vstemplate in Visual Studio.  

4.  Per un progetto C# di Windows universale, nel file vstemplate aggiungere il codice XML seguente all'interno del tag `<TemplateData>` di apertura: `<TemplateID>Microsoft.CSharp.Class</TemplateID>`. 

    Per un progetto C# di Windows 8.1 Store, nel file vstemplate aggiungere il codice XML seguente all'interno del tag di apertura e chiusura `<TemplateData>` : `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`.  

    Un progetto C# di Windows 8.1 Store usa un valore `WinRT-Native-6.3`. Per Windows 10 e per altri tipi di progetto, vedere [Elemento TemplateGroupID (modelli di Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md).  

    Nell'esempio seguente è indicato l'intero contenuto di un file vstemplate dopo che è stata aggiunta la riga di codice XML `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`. Questo esempio è specifico per i progetti C#. È possibile modificare gli elementi <ProjectTpe> e \< [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)> per specificare altri tipi di progetto e di linguaggio.  

    ```xml  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>MyItemStoreTemplate.xaml</DefaultName>  
        <Name>MyItemStoreTemplate</Name>  
        <Description>This is an example itemtemplate</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>10</SortOrder>  
        <Icon>__TemplateIcon.ico</Icon>  
        <TemplateGroupID>WinRT-Managed</TemplateGroupID>  
      </TemplateData>  
      <TemplateContent>  
        <References />  
        <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>  
        <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  

     Per gli altri possibili valori di TemplateGroupID, vedere [Elemento TemplateGroupID (modelli di Visual Studio](../extensibility/templategroupid-element-visual-studio-templates.md)). Per il riferimento completo al file con estensione vstemplate, vedere [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)  

5.  In Visual Studio salvare e chiudere il file vstemplate.  

6.  Copiare e incollare il file vstemplate nel file ZIP incluso nella cartella ..Utenti\\*nomeutente*\Documenti\Visual Studio *versione*\Templates\ItemTemplates\.  

     Se viene visualizzata la finestra di dialogo **Copia file**, selezionare l'opzione **Copia e sostituisci**.  

 È ora possibile aggiungere un elemento basato su questo modello a un progetto [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] tramite la finestra di dialogo **Aggiungi nuovo elemento**.  

 Per altre informazioni sui nomi dei parametri, vedere [Parametri di modello](../ide/template-parameters.md).  
  
 
### <a name="enable_templates"></a>Per abilitare i modelli per sottotipi di progetto specifici  

1.  L'ambiente di sviluppo consente di rendere disponibili gli elementi di progetto nella finestra di dialogo Aggiungi elemento di determinati progetti. Usare questa procedura per rendere disponibili elementi personalizzati per progetti Windows, Web, Office o di database.  

     Individuare l'elemento ProjectType nel file vstemplate per il modello di elemento.  

     Aggiungere un elemento [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) immediatamente dopo l'elemento ProjectType.  

2.  Impostare il valore di testo dell'elemento su uno dei valori seguenti:  

    1.  WINDOWS  

    2.  Office  

    3.  Database  

    4.  Web  

     Ad esempio: `<ProjectSubType>Database</ProjectSubType>`.  

     L'esempio seguente mostra un modello di elemento disponibile per i progetti Office.  

    ```  
    <VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">  
        <TemplateData>  
            <Name>Class</Name>  
            <Description>An empty class file</Description>  
            <Icon>Class.ico</Icon>  
            <ProjectType>CSharp</ProjectType>  
            <ProjectSubType>Office</ProjectSubType>  
            <DefaultName>Class.cs</DefaultName>  
        </TemplateData>  
        <TemplateContent>  
            <ProjectItem>Class1.cs</ProjectItem>  
        </TemplateContent>  
    </VSTemplate>  

    ```  

### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Per creare manualmente un modello di elemento senza usare l'Esportazione guidata modelli  

1.  Creare un progetto e un elemento di progetto.  

2.  Modificare l'elemento di progetto finché non è pronto per essere salvato come modello.  

3.  Modificare il file del codice come appropriato per indicare dove deve avvenire la sostituzione dei parametri. Per altre informazioni sulla sostituzione dei parametri, vedere [Procedura: Sostituire i parametri di un modello.](../ide/how-to-substitute-parameters-in-a-template.md)

4.  Creare un file XML e salvarlo con estensione vstemplate nella stessa directory del nuovo modello di elemento.  

5.  Creare il file XML vstemplate per fornire i metadati del modello di elemento. Per altre informazioni, vedere [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md) e l'esempio nella sezione precedente.  

6.  Salvare e chiudere il file vstemplate.  

7.  In Esplora risorse selezionare i file da includere nel modello, fare clic con il pulsante destro del mouse sulla selezione, scegliere Invia a, quindi Cartella compressa. I file selezionati verranno compressi in un file ZIP.  

8.  Copiare il file ZIP e incollarlo nel percorso dei modelli di elemento dell'utente. In Visual Studio 2017, la directory predefinita è... \Utenti\\<nomeutente\>\Documenti\Visual Studio 2017\Templates\ItemTemplates\\. Per altre informazioni, vedere Procedura: individuare e organizzare modelli di progetto e modelli di elementi.  

## <a name="see-also"></a>Vedere anche  
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Procedura: Creare modelli di elementi a più file](../ide/how-to-create-multi-file-item-templates.md)   
 [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
