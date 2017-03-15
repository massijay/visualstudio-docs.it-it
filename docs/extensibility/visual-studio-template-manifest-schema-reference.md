---
title: Modello di Visual Studio Manifest Schema Reference | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
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
ms.openlocfilehash: 0f4abf286dc8b1cf00e47468ddaa4831747a059d
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-template-manifest-schema-reference"></a>Riferimenti dello Schema del manifesto modello Visual Studio
Questo schema descrive il formato di file di manifesto (.vstman) modello di Visual Studio generati per i modelli di progetto o un elemento di Visual Studio e descrive la posizione e altre informazioni rilevanti relative al modello.  
  
 : Perché sono presenti elementi separati e le directory di progetto, un manifesto mai deve contenere una combinazione dei modelli di elemento e progetto.  
  
> [!IMPORTANT]
>  È disponibile a partire da Visual Studio 2017.  
  
## <a name="vstemplatemanifest-element"></a>Elemento VSTemplateManifest  
 L'elemento radice del manifesto.  
  
### <a name="attributes"></a>Attributi  
  
-   **Versione**: stringa che rappresenta la versione del manifesto del modello. Obbligatorio.  
  
-   **Impostazioni locali**: stringa che rappresenta le impostazioni locali o le impostazioni locali del manifesto del modello. Il valore delle impostazioni locali si applica a tutti i modelli, è necessario utilizzare un manifesto distinto per ciascuna lingua. Facoltativo.  
  
### <a name="child-elements"></a>Elementi figlio  
  
-   **VSTemplateContainer** facoltativo.  
  
-   **VSTemplateDir** facoltativo.  
  
### <a name="parent-element"></a>Elemento padre  
 Nessuno.  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Il contenitore del modello di elementi del manifesto. Un contenitore di modello per ogni modello che definisce un manifesto.  
  
### <a name="attributes"></a>Attributi  
 **VSTemplateType** : un valore stringa che specifica il tipo di modello (`"Project"`, `"Item"`, o `"ProjectGroup"`). Richiesto  
  
### <a name="child-elements"></a>Elementi figlio  
  
-   **RelativePathOnDisk**: il percorso relativo del file di modello su disco. Questo percorso definisce anche la posizione del modello nell'albero del modello nella **nuovo progetto** o **nuovo elemento** finestra di dialogo. Per i modelli distribuiti come singoli file e una directory, questo percorso fa riferimento alla directory contenente i file di modello. Per i modelli distribuiti come file ZIP, questo percorso deve essere il percorso del file con estensione zip.  
  
-   **VSTemplateHeader** : un [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento che descrive l'intestazione.  
  
### <a name="parent-element"></a>Elemento padre  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Descrive la directory in cui si trova il modello. Un manifesto può contenere più **VSTemplateDir** voci per fornire nome localizzato e ordinamento per le directory di ordinamento per determinarne l'aspetto nella struttura di categoria di modello.  
  
 A causa di progettazione, **VSTemplateDir** voci dovrebbero essere visualizzato solo nei manifesti specificati non locali.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
-   **RelativePath**: il percorso del modello. Può esistere solo una voce per ogni percorso, il primo avrà la precedenza per tutti i manifesti.  
  
-   **LocalizedName**: un **NameDescriptionIcon** elemento che specifica il nome localizzato. Facoltativo.  
  
-   **SortOrder** : una stringa che specifica l'ordinamento. Facoltativo.  
  
-   **ParentFolderOverrideName**: il nome della cartella padre sottoposto a override. Facoltativo. Questo elemento ha un **nome** attributo, ovvero un valore stringa che specifica il nome.  
  
### <a name="parent-element"></a>Elemento padre  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Specifica il nome e descrizione, possibilmente per modelli localizzati. Vedere **LocalizedName** sopra.  
  
### <a name="attributes"></a>Attributi  
  
-   **Pacchetto**: un valore stringa che specifica il pacchetto. Facoltativo.  
  
-   **ID**: un valore stringa che specifica l'ID. Facoltativo.  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-element"></a>Elemento padre  
 **LocalizedName**  
  
## <a name="examples"></a>Esempi  
 Di seguito è riportato un esempio di un file di progetto modello .vstman.  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>  
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>TestProjectTemplate</Name>  
        <Description>TestProjectTemplate</Description>  
        <Icon>TestProjectTemplate.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>TestProjectTemplate</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Di seguito è riportato un esempio di un elemento .vstman del file di modello.  
  
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
