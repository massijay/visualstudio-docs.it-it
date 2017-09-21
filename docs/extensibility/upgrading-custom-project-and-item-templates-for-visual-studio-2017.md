---
title: Aggiornamento progetto personalizzati e modelli di elemento per Visual Studio &quot;15&quot; | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: af2000e6c3649b625c54ed9dc2706d64642016ad
ms.lasthandoff: 02/22/2017

---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>Aggiornamento progetto personalizzato e i modelli di Visual Studio 2017
A partire da Visual Studio 2017, Visual Studio è modificare la modalità consente di individuare modelli di progetto e di elemento che è stati installati da un VSIX o un file con estensione msi. Se si dispone di estensioni che utilizzano modelli di elemento o progetto personalizzato, è necessario aggiornare le estensioni. In questo argomento vengono illustrate le operazioni da eseguire.  
  
 Questa modifica interessa solo Visual Studio 2017. Non influisce le versioni precedenti di Visual Studio.  
  
 Se si desidera creare un modello di progetto o un elemento come parte di un'estensione VSIX, vedere [creazione progetto personalizzati e modelli di elemento](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Modello di analisi  
 In precedenza, **devenv /setup** o **devenv /installvstemplates** analizzati nel disco locale per trovare i modelli di progetto e di elemento. A partire da 4 di anteprima, l'analisi verrà eseguita solo per il percorso a livello utente (**%USERPROFILE%\Documents\\<Visual studio=""></Visual>\>\My Exported Templates\\**) utilizzato per i modelli generati dal **File / esportare modelli** comando.  
  
 Per altre posizioni (non-utente), è necessario includere un file manifest(.vstman) che specifica la posizione e altre caratteristiche del modello. Viene generato il file .vstman insieme al file. vstemplate utilizzato per i modelli. Se si installa l'estensione utilizzando un'estensione VSIX, è possibile farlo ricompilando l'estensione in Visual Studio 2017. Ma se si utilizza un file con estensione msi, è necessario apportare le modifiche manualmente. Per un elenco di ciò che occorre per apportare queste modifiche, vedere **aggiornamenti per estensioni installate con un. MSI** più avanti in questo argomento.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Come aggiornare un'estensione VSIX con modelli di elemento o progetto  
 Questa procedura viene descritto come ottenere Visual Studio 2017
1.  Aprire la soluzione in Visual Studio 2017. Verrà richiesto di aggiornare il codice. Fare clic su **OK**.  
  
2.  Al termine dell'aggiornamento, potrebbe essere necessario modificare la versione della destinazione dell'installazione. Nel progetto VSIX, aprire il file source.extension.vsixmanifest e selezionare il **destinazioni di installazione** scheda. Se il **intervallo versione** campo **[14.0]**, fare clic su **modificare** e modificarla per includere 2017 di Visual Studio. Ad esempio, è possibile impostare **[14.0,15.0]** per installare l'estensione di Visual Studio 2015 o Visual Studio 2017, o di **[15.0]** installarlo solo Visual Studio 2017.  
  
3.  Ricompilare il codice.  
  
4.  Chiudere Visual Studio.  
  
5.  Installare il pacchetto VSIX.  
  
6.  È possibile testare l'aggiornamento eseguendo le operazioni seguenti:  
  
    1.  Il file di analisi di modifica viene attivato dalla chiave del Registro di sistema seguente:  
  
         **REG aggiungere hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Dopo aver aggiunto la chiave, eseguire **devenv /installvstemplates**.  
  
    3.  Chiudere e riaprire Visual Studio. Trovare il modello nel percorso previsto.  
  
    > [!NOTE]
    >  I modelli di progetto di estensibilità di Visual Studio non sono disponibili quando è presente la chiave del Registro di sistema. È necessario eliminare la chiave del Registro di sistema (e rieseguire **devenv /installvstemplates**) come utilizzarli.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Altri suggerimenti per la distribuzione di progetto e modelli di elemento  
  
-   Evitare di utilizzare file di modello compresso. Compressi modello file devono essere compressi per recuperare le risorse e il contenuto, pertanto saranno costlier da utilizzare. In alternativa, è necessario distribuire modelli di progetto e di elemento come singoli file con le proprie directory per velocizzare l'inizializzazione di modello. Per le estensioni VSIX, attività di compilazione SDK decomprimerà automaticamente qualsiasi modello compresso durante la creazione del file VSIX.  
  
-   Evitare di utilizzare le voci ID pacchetto/risorse per il nome del modello, descrizione, icona o anteprima per evitare i caricamenti di assembly di risorse non necessari durante l'individuazione del modello. In alternativa, è possibile utilizzare manifesti localizzati per creare una voce di modello per ogni lingua, che utilizza i nomi localizzati o proprietà.  
  
-   Se si desidera includere modelli come elementi di file, la generazione del manifesto potrebbe non lasciare i risultati previsti. In tal caso, è necessario aggiungere un manifesto generato manualmente al progetto VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Modifiche ai file nel progetto e modelli di elemento  
 I punti della differenza tra la versione di Visual Studio 2015 e la versione di Visual Studio "15" dei file di modello, verrà illustrato in modo che sia possibile creare nuovi file in modo corretto.  
  
 Ecco il file. vstemplate di progetto predefinito creato da Visual Studio 2015:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ProjectTemplate1</Name>  
    <Description>ProjectTemplate1</Description>  
    <Icon>ProjectTemplate1.ico</Icon>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <SortOrder>1000</SortOrder>  
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
    <CreateNewFolder>true</CreateNewFolder>  
    <DefaultName>ProjectTemplate1</DefaultName>  
    <ProvideDefaultName>true</ProvideDefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">  
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>  
    </Project>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 Ecco il file .vstman (è possibile trovarlo nella directory del manifesto del progetto VSIX) che causa la ricompilazione del progetto VSIX:  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ProjectTemplate1</Name>  
        <Description>ProjectTemplate1</Description>  
        <Icon>ProjectTemplate1.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>ProjectTemplate1</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Le informazioni fornite di [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento rimane invariato. Il ** \<VSTemplateContainer >** elemento punta ai file. vstemplate del modello associato.  
  
 Ecco il file. vstemplate elemento predefinito creato da Visual Studio 2015:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ItemTemplate1</Name>  
    <Description>ItemTemplate1</Description>  
    <Icon>ItemTemplate1.ico</Icon>  
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    <DefaultName>Class.cs</DefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <References>  
      <Reference>  
        <Assembly>System</Assembly>  
      </Reference>  
    </References>  
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 Ecco il file .vstman (è possibile trovarlo nella directory del manifesto del progetto VSIX) che causa la ricompilazione del progetto VSIX:  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Le informazioni fornite di ** \<TemplateData >** elemento rimane invariato. Il ** \<VSTemplateContainer >** elemento punta ai file. vstemplate del modello associato  
  
 Per ulteriori informazioni sui diversi elementi del file .vstman, vedere [Visual Studio modello Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Gli aggiornamenti per le estensioni installate con un. FILE MSI  
 Alcune estensioni basate su MSI distribuire modelli di posizioni di modelli comuni, tra cui:  
  
-   **\<Directory di installazione di Visual Studio > \Common7\IDE.\\<ProjectTemplates temtemplates="">**</ProjectTemplates>  
  
-   **\<Directory di installazione di Visual Studio > \Common7\IDE\Extensions\\<>\>\\<Project temtemplates="">**</Project>  
  
 Se l'estensione viene eseguita una distribuzione basata su MSI, è necessario generare manualmente manifesto del modello e assicurarsi che sia incluso nel programma di installazione di estensione. È necessario confrontare gli esempi .vstman elencati in precedenza e [Visual Studio modello Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md). Per vedere cosa è necessario includere  
  
 È consigliabile creare manifesti distinti per i modelli di progetto e di elemento e deve puntare modello radice come specificato sopra. È necessario creare un manifesto per l'estensione e le impostazioni locali.  
  
## <a name="troubleshooting-template-installation"></a>Risoluzione dei problemi di installazione del modello  
 Se si verificano problemi durante la distribuzione dei modelli di progetto o un elemento, è possibile abilitare la registrazione diagnostica.  
  
1.  Eseguire il comando seguente per impostare la chiave del Registro di sistema per abilitare la registrazione:  
  
     **REG aggiungere HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate /v EnableTemplateDiscoveryLog /t REG_DWORD /d 1**  
  
2.  Avviare Visual Studio e avviare le finestre di dialogo Nuovo elemento e nuovo progetto per inizializzare due alberi di modello. Il log di modello viene visualizzato nel **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**. Ogni inizializzazione di struttura ad albero del modello aggiunge voci al log.  
  
 Il file di log contiene le colonne seguenti:  
  
-   **FullPathToTemplate**, che presenta i seguenti valori:  
  
    -   1 per la distribuzione basata su manifesto  
  
    -   0 per la distribuzione basata su disco  
  
-   **TemplateFileName**  
  
-   Altre proprietà del modello
