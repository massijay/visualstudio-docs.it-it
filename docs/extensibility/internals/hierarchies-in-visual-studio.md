---
title: Le gerarchie in Visual Studio | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 14
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
ms.openlocfilehash: ca8fa51a14f38dcd651f26e8ed10ca48d670f37b
ms.lasthandoff: 02/22/2017

---
# <a name="hierarchies-in-visual-studio"></a>Gerarchie in Visual Studio
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) consente di visualizzare un progetto come un *gerarchia*. Nell'IDE di una gerarchia è una struttura ad albero di nodi, in cui ogni nodo dispone di un set di proprietà associate. Oggetto *gerarchia del progetto* è un contenitore che contiene gli elementi del progetto, relazioni, gli elementi e proprietà associate gli elementi e comandi.  
  
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], gestire le gerarchie di progetto utilizzando l'interfaccia di gerarchia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>interfaccia reindirizza comandi richiamare da elementi di progetto nella finestra gerarchia appropriata anziché il gestore di comandi standard.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>  
  
## <a name="project-hierarchies"></a>Gerarchie di progetto  
 Ogni gerarchia del progetto contiene elementi che è possibile visualizzare e modificare. Questi elementi variano a seconda del tipo di progetto. Ad esempio, un progetto di database potrebbe contenere stored procedure, viste di database e tabelle di database. Un progetto di linguaggio di programmazione, d'altra parte, probabilmente includerà i file di origine e file di risorse per finestre di dialogo e bitmap. Le gerarchie possono essere annidate, che offre una maggiore flessibilità quando si crea una gerarchia del progetto.  
  
 Quando si crea un nuovo tipo di progetto, il tipo di progetto consente di controllare il set completo di elementi che può essere modificato in essa contenuti. Tuttavia, i progetti possono contenere elementi per cui non dispongano di supporto per la modifica. Ad esempio, i progetti Visual C++ possono contenere i file HTML, anche se Visual C++ non fornisce un editor personalizzato per il tipo di file HTML.  
  
 Gerarchie di gestiscono la persistenza di elementi in essi contenuti. L'implementazione della gerarchia deve controllare le proprietà speciali che interessano la persistenza degli elementi all'interno della gerarchia. Ad esempio, se gli elementi rappresentano gli oggetti in un repository anziché i file, l'implementazione di gerarchia deve controllare la persistenza di tali oggetti. L'IDE stesso indirizza la gerarchia per salvare gli elementi in conformità con l'input dell'utente, ma l'IDE non controlla le eventuali azioni necessarie per salvare tali elementi. Al contrario, il progetto è nel controllo.  
  
 Quando un utente apre un elemento in un editor, la gerarchia dei controlli di tale elemento viene selezionata e diventa la gerarchia di active. La gerarchia selezionata determina il set di comandi disponibili per intervenire sull'elemento. Rilevamento stato attivo in questo modo consente la gerarchia riflettere il contesto dell'utente corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di progetto](../../extensibility/internals/project-types.md)   
 [Selezione e la valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Esempi di VSSDK](../../misc/vssdk-samples.md)
