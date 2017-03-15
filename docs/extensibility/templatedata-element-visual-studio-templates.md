---
title: Elemento TemplateData (modelli di Visual Studio) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 185734d82820c8de0d84e995e2ff88894a2c86dc
ms.lasthandoff: 02/22/2017

---
# <a name="templatedata-element-visual-studio-templates"></a>Elemento TemplateData (modelli di Visual Studio)
Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .  
  
 \<VSTemplate >  
 \<TemplateData >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Nome](../extensibility/name-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica il nome del modello come appare in entrambi i **nuovo progetto** o **Aggiungi nuovo elemento** la finestra di dialogo.|  
|[Descrizione](../extensibility/description-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica la descrizione del modello come appare in entrambi i **nuovo progetto** o **Aggiungi nuovo elemento** la finestra di dialogo.|  
|[Icona](../extensibility/icon-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica il percorso e il nome del file di immagine che funge da icona, viene visualizzata in uno di **nuovo progetto** o **Aggiungi nuovo elemento** della finestra di dialogo per il modello.|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello di progetto in modo che venga visualizzata sotto il gruppo specificato di **nuovo progetto** la finestra di dialogo.|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Classifica il modello di progetto in modo che venga visualizzato nella sottocategoria specificata nella finestra di **nuovo progetto** la finestra di dialogo.|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica l'ID modello.|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica l'ID del gruppo di modello.|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica un valore che viene utilizzato per disporre il modello, tra gli altri modelli nella stessa categoria, così come appare in entrambi i **nuovo progetto** o **Aggiungi nuovo elemento** la finestra di dialogo.|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica se in fase di creazione del progetto viene creata una cartella che lo contiene.|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica il nome che verrà generato il sistema del progetto di Visual Studio per il progetto o un elemento quando viene creato.|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica se il sistema del progetto di Visual Studio genera il nome predefinito per un progetto o un elemento quando viene creato.|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica se è possibile creare il progetto come progetto temporaneo.|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica se il **Sfoglia** pulsante è disponibile nel **nuovo progetto** nella finestra di dialogo, in modo che gli utenti possono facilmente modificare la directory predefinita in cui viene salvato un nuovo progetto.|  
|[Nascosto](../extensibility/hidden-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica se il modello viene visualizzato in entrambi i **nuovo progetto** o **Aggiungi nuovo elemento** la finestra di dialogo.|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica il numero di categorie principali che verrà visualizzato il modello di **nuovo progetto** la finestra di dialogo.|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|Elemento facoltativo.|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|Elemento facoltativo.<br /><br /> Consente di specificare o meno il **percorso** casella di testo il **nuovo progetto** la finestra di dialogo abilitata, disabilitata o nascosta per il modello di progetto.|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Utilizzare questo elemento se il modello supporta solo una versione minima specifica e versioni successive di .NET Framework.|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica se il modello supporta una pagina master per i progetti web.|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica se il modello supporta la separazione del codice o il modello di pagina code-behind, per i progetti web.|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica se il modello è identico per più linguaggi e se il **Language** opzione è disponibile il **nuovo progetto** la finestra di dialogo.|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Specifica la piattaforma a cui è destinato il modello di progetto. Questo elemento specifica un modello di progetto viene utilizzato per creare [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Contiene tutti i metadati per il modello di progetto modello di elemento o lo starter kit.|  
  
## <a name="remarks"></a>Note  
 `TemplateData`è un elemento obbligatorio.  
  
 Se non si include un elemento facoltativo, viene utilizzato il valore predefinito per tale elemento.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra i metadati per un modello di progetto per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] dell'applicazione.  
  
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
            <ProjectItem>Form1.cs<ProjectItem>  
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
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
