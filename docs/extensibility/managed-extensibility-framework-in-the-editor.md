---
title: Managed Extensibility Framework nell&quot;Editor | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 10
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
ms.openlocfilehash: 6a5cb0ae0f8da6af939588ad358e6b5b1b3b108e
ms.lasthandoff: 02/22/2017

---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework nell'Editor
L'editor è integrato con i componenti di Managed Extensibility Framework (MEF). È possibile compilare i componenti MEF per estendere l'editor e il codice può utilizzare anche i componenti dell'editor.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Panoramica di Managed Extensibility Framework  
 La libreria MEF è una libreria .NET che consente di aggiungere e modificare le funzionalità di un'applicazione o componente che segue il modello di programmazione MEF. Editor di Visual Studio può sia forniscono e utilizzano i componenti MEF.  
  
 La libreria MEF è contenuta nell'assembly .NET Framework versione 4 System.ComponentModel.Composition.dll.  
  
 Per ulteriori informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Componenti e contenitori di composizione  
 Un componente è una classe o un membro di una classe che può eseguire una (o entrambe) delle operazioni seguenti:  
  
-   Utilizzare un altro componente  
  
-   Essere utilizzati da un altro componente  
  
 Ad esempio, si consideri un'applicazione di acquisti che dispone di un componente di voce dell'ordine che dipende dai dati di disponibilità del prodotto forniti da un componente di inventario di magazzino. In termini MEF, la parte di magazzino può *esportare* dati sulla disponibilità del prodotto e ordine voce parte può *importare* i dati. La parte di voce dell'ordine e la parte di magazzino non è necessario conoscere a vicenda. il *contenitore di composizione* (fornito dall'applicazione host) è responsabile mantenendo l'insieme di esportazioni e risolvere le esportazioni e importazioni.  
  
 Il contenitore di composizione, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, in genere è di proprietà dell'host.</xref:System.ComponentModel.Composition.Hosting.CompositionContainer> Il contenitore di composizione conserva un *catalogo* dei componenti esportati.  
  
### <a name="exporting-and-importing-component-parts"></a>Esportazione e importazione di componenti  
 È possibile esportare qualsiasi funzionalità, come viene implementato come una classe pubblica o un membro pubblico di una classe (proprietà o metodo). Non è necessario derivare il componente <xref:System.ComponentModel.Composition.Primitives.ComposablePart>.</xref:System.ComponentModel.Composition.Primitives.ComposablePart> In alternativa, è necessario aggiungere un <xref:System.ComponentModel.Composition.ExportAttribute>attributo alla classe o membro di classe che si desidera esportare.</xref:System.ComponentModel.Composition.ExportAttribute> Questo attributo specifica il *contratto* dal componente in cui un'altra parte possibile importare la funzionalità.  
  
### <a name="the-export-contract"></a>Il contratto di esportazione  
 Il <xref:System.ComponentModel.Composition.ExportAttribute>definisce l'entità (classe, interfaccia o struttura) che viene esportata.</xref:System.ComponentModel.Composition.ExportAttribute> In genere, l'attributo export accetta un parametro che specifica il tipo dell'esportazione.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Per impostazione predefinita, l' <xref:System.ComponentModel.Composition.ExportAttribute>attributo definisce un contratto che è il tipo di classe di esportazione.</xref:System.ComponentModel.Composition.ExportAttribute>  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 Nell'esempio, il valore predefinito `[Export]` è equivalente all'attributo `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 È inoltre possibile esportare una proprietà o metodo, come illustrato nell'esempio seguente.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>Importazione di un'esportazione MEF  
 Quando si desidera utilizzare un'esportazione MEF, è necessario conoscere il contratto (in genere del tipo) da cui è stato esportato e aggiungere un <xref:System.ComponentModel.Composition.ImportAttribute>attributo con tale valore.</xref:System.ComponentModel.Composition.ImportAttribute> Per impostazione predefinita, l'attributo import accetta un parametro, ovvero il tipo della classe che viene modificato. Le seguenti righe di importazione di codice il <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>tipo.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Recupero di funzionalità dell'Editor da un componente MEF  
 Se il codice esistente è un componente MEF, è possibile utilizzare i metadati MEF per utilizzare l'editor di componenti.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Per utilizzare la funzionalità di editor da un componente MEF  
  
1.  Aggiungere riferimenti a System.Composition.ComponentModel.dll, presente nella global assembly cache (GAC), e agli assembly dell'editor.  
  
2.  Aggiungere le relative istruzioni using.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Aggiungere il `[Import]` attributo all'interfaccia di servizio, come indicato di seguito.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Dopo aver ottenuto il servizio, è possibile utilizzare uno qualsiasi dei relativi componenti.  
  
5.  Quando è stato compilato l'assembly, lo script nel... Cartella \Common7\IDE\Components\ dell'installazione di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Servizio di linguaggio e punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md)
