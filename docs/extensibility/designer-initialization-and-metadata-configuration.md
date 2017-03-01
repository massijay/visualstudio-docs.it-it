---
title: Inizializzazione della finestra di progettazione e configurazione dei metadati | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 16
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c0865b62cc2683a8197b5eb6cbc0599d6c063534
ms.lasthandoff: 02/22/2017

---
# <a name="designer-initialization-and-metadata-configuration"></a>Inizializzazione della finestra di progettazione e configurazione dei metadati
Modifica degli attributi dei metadati e il filtro associato a un componente della finestra di progettazione o la finestra di progettazione fornisce un meccanismo per le applicazioni definire quali strumenti vengono utilizzati da una particolare finestra di progettazione per gestire diversi <xref:System.Type>oggetti (ad esempio strutture dei dati, classi o le entità con interfaccia grafiche), quando è disponibile la progettazione e come l'IDE di Visual Studio è configurato per supportare la finestra di progettazione (per l'istanza che **della casella degli strumenti** categoria o la scheda è disponibile).</xref:System.Type>  
  
 Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] offre diversi meccanismi per facilitare il controllo dell'inizializzazione di una finestra di progettazione o del componente della finestra di progettazione e la modifica dei metadati da un VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Inizializzazione di metadati e le informazioni di configurazione  
 Poiché vengono caricati su richiesta, i package VS potrebbe non sono stati caricati dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente prima di creare un'istanza di una finestra di progettazione. Quindi package VS possibile utilizzare il meccanismo standard per la configurazione di un componente della finestra di progettazione o la finestra di progettazione al momento della creazione, ovvero per gestire un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>eventi.</xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> Invece, un VSPackage implementa un'istanza di <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>l'interfaccia e registrato in modo da fornire personalizzazioni, detta estensioni della superficie di progettazione.</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
### <a name="customizing-initialization"></a>Personalizzazione di inizializzazione  
 Personalizzazione di una finestra di progettazione, un componente o un'area di progettazione, prevede:  
  
1.  Modifica i metadati della finestra di progettazione e la modifica in modo efficace come una certa <xref:System.Type>venga eseguito o convertiti.</xref:System.Type>  
  
     Questa operazione viene in genere eseguita tramite il <xref:System.Drawing.Design.UITypeEditor>o <xref:System.ComponentModel.TypeConverter>meccanismi.</xref:System.ComponentModel.TypeConverter> </xref:System.Drawing.Design.UITypeEditor>  
  
     Ad esempio, quando <xref:System.Windows.Forms>-finestre di progettazione in base vengono inizializzati, il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente modifica il <xref:System.Drawing.Design.UITypeEditor>per <xref:System.Web.UI.WebControls.Image>oggetti utilizzati con la finestra di progettazione per utilizzare il gestore di risorse per ottenere le immagini bitmap anziché nel file system.</xref:System.Web.UI.WebControls.Image> </xref:System.Drawing.Design.UITypeEditor> </xref:System.Windows.Forms>  
  
2.  L'integrazione con l'ambiente, ad esempio, per la sottoscrizione di eventi o per ottenere informazioni sulla configurazione di progetto. È possibile ottenere informazioni sulla configurazione di progetto e sottoscrivere eventi ottenendo il <xref:System.ComponentModel.Design.ITypeResolutionService>interfaccia.</xref:System.ComponentModel.Design.ITypeResolutionService>  
  
3.  Modifica dell'ambiente utente attivando appropriato **della casella degli strumenti** categorie o limitare l'applicabilità della finestra di progettazione tramite l'applicazione di un'istanza della <xref:System.ComponentModel.ToolboxItemFilterAttribute>classe nella finestra di progettazione.</xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
### <a name="designer-initialization-by-a-vspackage"></a>Inizializzazione della finestra di progettazione da un VSPackage  
 Un VSPackage deve gestire l'inizializzazione della finestra di progettazione per:  
  
1.  Creazione di un oggetto che implementa la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>classe.</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
    > [!NOTE]
    >  L' <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>classe non deve essere implementata mai sullo stesso oggetto come <xref:Microsoft.VisualStudio.Shell.Package>classe.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
2.  Registrare la classe di implementazione di <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>come fornire supporto per le estensioni della finestra di progettazione del VSPackage applicando le istanze di <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>e <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>alla classe che fornisce l'implementazione del VSPackage <xref:Microsoft.VisualStudio.Shell.Package>.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
 Ogni volta che viene creato qualsiasi finestra di progettazione o di un componente della finestra di progettazione, il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente:  
  
1.  Accede a ogni provider di estensione della superficie di progettazione registrato.  
  
2.  Crea e inizializza un'istanza del provider di estensione della superficie ogni struttura <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>oggetto</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
3.  Chiama ogni provider di estensione della superficie di progettazione <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>metodo o <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>(metodo) (come appropriato).</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>  
  
 Quando si implementa il <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>dell'oggetto come un membro di un package VS, è importante comprendere che:</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
1.  Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente non fornisce alcun controllo su quali i metadati o altre impostazioni di configurazione una particolare `DesignSurfaceExtension` modifica del provider. È possibile che due o più `DesignSurfaceExtension` provider modifica la stessa funzionalità della finestra di progettazione in modalità in conflitto, la modifica finale da definitivo. È indeterminato quale modifica viene applicata.  
  
2.  È possibile limitare in modo esplicito un'implementazione di <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>specifiche finestre di progettazione, applicando le istanze di oggetto <xref:System.ComponentModel.ToolboxItemFilterAttribute>al tipo di implementazione.</xref:System.ComponentModel.ToolboxItemFilterAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Per ulteriori informazioni su **della casella degli strumenti** elemento filtro, vedere <xref:System.ComponentModel.ToolboxItemFilterAttribute>e <xref:System.ComponentModel.ToolboxItemFilterType>.</xref:System.ComponentModel.ToolboxItemFilterType> </xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
## <a name="additional-metadata-provisioning"></a>Provisioning di metadati aggiuntivi  
 Un pacchetto Visual Studio è possibile modificare la configurazione di una finestra di progettazione o un componente della finestra di progettazione diverso in fase di progettazione.  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>classe può essere utilizzata a livello di codice o essere applicato a un pacchetto che fornisce una finestra di progettazione.</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 Un'istanza di <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>classe viene utilizzata per modificare i metadati di componenti creati in un'area di progettazione.</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Ad esempio, una possibile sostituire un visualizzatore di proprietà predefinito utilizzato da <xref:System.Windows.Forms.CommonDialog>gli oggetti con un visualizzatore di proprietà personalizzato.</xref:System.Windows.Forms.CommonDialog>  
  
 Modifiche fornite da un'istanza di <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>applicata all'implementazione di un pacchetto di <xref:Microsoft.VisualStudio.Shell.Package>può avere uno dei due ambiti:</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
-   Globali - per tutte le nuove istanze di un determinato componente  
  
-   Locale - si riferisce solo all'istanza del componente creato nell'area di progettazione fornita da VSPackage corrente.  
  
 Il `IsGlobal` proprietà di <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>istanza applicata all'implementazione di un pacchetto di <xref:Microsoft.VisualStudio.Shell.Package>determina l'ambito.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 Applicando l'attributo a un'implementazione di <xref:Microsoft.VisualStudio.Shell.Package>con la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>proprietà del <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>oggetto impostato su `true`, come mostrato di seguito, viene modificato il browser per l'intero [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente:</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> </xref:Microsoft.VisualStudio.Shell.Package>  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Se il flag globale è stato impostato su `false`, la modifica dei metadati è locale per la finestra di progettazione corrente supportato dal VSPackage corrente:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  Attualmente, l'area di progettazione supporta solo la creazione di componenti, e pertanto solo i componenti possono avere metadati locali. Nell'esempio precedente, si stava tentando di modificare una proprietà, ad esempio la `Color` proprietà di un oggetto. Se `false` passato per il flag globale, `CustomBrowser` non verranno visualizzati perché la finestra di progettazione crea mai un'istanza di `Color`. Impostare il flag globale `false` è utile per i componenti, ad esempio controlli, timer e le finestre di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType></xref:System.ComponentModel.ToolboxItemFilterType>   
 [Estensione del supporto in fase di progettazione](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
