---
title: Fornisce l&quot;automazione di VSPackages | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 15
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ca3700d1e26ccd4be1054463e9426b364ba17301
ms.lasthandoff: 02/22/2017

---
# <a name="providing-automation-for-vspackages"></a>Fornisce l'automazione per i package VS
Esistono due modi per consentire l'automazione per il package VS: implementando oggetti specifici di un VSPackage e implementando gli oggetti di automazione standard. In genere, questi vengono utilizzati insieme per estendere il modello di automazione dell'ambiente.  
  
## <a name="vspackage-specific-objects"></a>Oggetti specifici di VSPackage  
 Determinate posizioni all'interno del modello di automazione è necessario fornire gli oggetti di automazione che sono univoci per il pacchetto Visual Studio. Ad esempio, i nuovi progetti richiedono oggetti distinti che fornisce solo il pacchetto Visual Studio. I nomi di questi oggetti vengono immessi nel Registro di sistema e ottenuti tramite chiamate all'ambiente `DTE` oggetto.  
  
 È possibile ottenere gli oggetti specifici di VSPackage anche quando un consumer di automazione viene utilizzato l'oggetto fornito tramite la proprietà dell'oggetto di un oggetto standard. Ad esempio, lo standard `Window` oggetto ha un `Object` proprietà, comunemente noto come il `Windows.Object` proprietà. Quando i consumer chiamano il `Window.Object` in una finestra implementata nel pacchetto Visual Studio, passare nuovamente un oggetto di automazione specifico di propria progettazione.  
  
#### <a name="projects"></a>Progetti  
 Package VS possono estendere il modello di automazione per i nuovi tipi di progetto tramite i propri oggetti VSPackage specifici. Lo scopo principale di fornire i nuovi oggetti di automazione per il pacchetto Visual Studio è possibile distinguere il progetto univoco gli oggetti da un <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject>o <xref:VSLangProj80.VSProject2>oggetto.</xref:VSLangProj80.VSProject2> </xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> Questa distinzione è utile quando si desidera fornire un modo per singola o il tipo di progetto a parte di altri tipi di progetto, eseguire l'iterazione deve appaiono side-by-side in una soluzione. Per ulteriori informazioni, vedere [esposizione di oggetti del progetto](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Eventi  
 L'architettura di evento dell'ambiente offre un'altra posizione in cui aggiungere gli oggetti specifici di VSPackage. Tramite la creazione di oggetti evento univoco, ad esempio, è possibile estendere il modello di eventi dell'ambiente per i progetti. Si potrebbe voler fornire i propri eventi quando viene aggiunto un nuovo elemento al tipo di progetto. Per ulteriori informazioni, vedere [esposizione di eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Oggetti finestra  
 Windows può passare nuovamente un oggetto di automazione specifico VSPackage nell'ambiente quando viene chiamato. Si implementa un oggetto derivato da <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject>o `IDispatch` che passa nuovamente le proprietà, si estende la classe di finestra in cui viene individuato.</xref:EnvDTE.IExtensibleObject> </xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> Ad esempio, è possibile utilizzare questo approccio per consentire l'automazione per un controllo individuato in una cornice di finestra. La semantica di questo oggetto e altri oggetti che è possibile estendere è quelle in uso per la progettazione. Per ulteriori informazioni, vedere [procedura: fornire l'automazione per Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Pagine delle opzioni del menu Strumenti  
 È possibile creare pagine per estendere gli strumenti, modello di automazione opzioni tramite l'implementazione delle pagine e aggiungere informazioni al Registro di sistema per creare le proprie opzioni. Sono quindi possibile chiamare le pagine tramite il modello a oggetti ambiente come tutte le altre pagine di opzioni. Se la progettazione della funzionalità di cui che si sta aggiungendo l'ambiente tramite i package VS richiede le pagine di opzioni, è necessario aggiungere anche il supporto di automazione. Per ulteriori informazioni, vedere [supporto di automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Oggetti di automazione standard  
 Per estendere l'automazione per i progetti, si implementano anche gli oggetti di automazione standard (derivato da `IDispatch`) che indicano accanto ad altri oggetti di progetto e implementare i metodi e proprietà standard. Esempi di oggetti standard sono gli oggetti di progetto che vengono inseriti nella gerarchia della soluzione, ad esempio `Projects`, `Project`, `ProjectItem`, e `ProjectItems`. Ogni nuovo tipo di progetto deve implementare questi oggetti (e possibilmente altri in base alla semantica del progetto).  
  
 In un certo senso, questi oggetti forniscono il vantaggio degli oggetti di progetto VSPackage specifiche opposto. Gli oggetti di automazione standard consentono il progetto da utilizzare in modo generalizzato come qualsiasi altro progetto che supporta gli stessi oggetti. Pertanto, un componente aggiuntivo che viene scritto in generale `Project` e `ProjectItem` gli oggetti possono funzionare con i progetti di qualsiasi tipo. Per ulteriori informazioni, vedere [progetto di modellazione](../../extensibility/internals/project-modeling.md).
