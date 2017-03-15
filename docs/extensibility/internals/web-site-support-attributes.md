---
title: Sito Web supporto attributi | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 9
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
ms.openlocfilehash: dba1aeb8f8e3ad368f050ef425f76cc6c94f99e8
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support-attributes"></a>Attributi di supporto del sito Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Progetto di sito Web può essere esteso per fornire supporto per Web linguaggi di programmazione. Il linguaggio deve registrarsi con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modo che i modelli di progetto possono essere visualizzati nel **nuovo sito Web** la finestra di dialogo quando si seleziona la lingua.  
  
 L'esempio IronPython Studio include il supporto del sito web. È possibile trovarlo con le [VSSDK esempi](../../misc/vssdk-samples.md). Include le classi di attributo seguente per registrare IronPython come lingua codebehind per nuovi progetti Web.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Questo attributo viene posizionato sul progetto di linguaggio. La lingua viene aggiunto all'elenco dei linguaggi di programmazione Web di **Language** nell'elenco di **nuovo sito Web** la finestra di dialogo. Ad esempio, il seguente aggiunge IronPython all'elenco:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Questo attributo imposta inoltre il percorso di modelli in modo che punti alla cartella templates. Per ulteriori informazioni sulla posizione della cartella modelli, vedere [modelli di sito Web supporto](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Questo attributo viene posizionato sul progetto di linguaggio. Consente il progetto di sito Web nidificare un tipo di file (correlato) in un altro tipo di file (principale) nel **Esplora**.  
  
 Ad esempio:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Specifica che un file codebehind di IronPython è correlato a un file aspx. Quando viene creata una nuova pagina Web aspx in una soluzione di sito Web di IronPython, un nuovo file di origine. py viene generato e visualizzato come nodo figlio della pagina aspx.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Questo attributo viene inserito nel pacchetto di progetto di linguaggio. Seleziona il provider di Intellisense per la lingua.  
  
 Ad esempio:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Specifica che un'istanza di PythonIntellisenseProvider, che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, devono essere creati su richiesta per fornire servizi di linguaggio.</xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>  
  
 L'implementazione di IVsIntellisenseProject gestisce riferimenti e il compilatore di linguaggio viene chiamato quando una pagina Web con il codice è richiesto ma non memorizzato nella cache.  
  
## <a name="see-also"></a>Vedere anche  
 [Sito Web di supporto](../../extensibility/internals/web-site-support.md)
