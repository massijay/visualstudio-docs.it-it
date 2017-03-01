---
title: Selezione oggetti di contesto | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 13
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
ms.openlocfilehash: 3fa5093ee38c364a4766160f8642755bc0b2a23f
ms.lasthandoff: 02/22/2017

---
# <a name="selection-context-objects"></a>Selezione oggetti di contesto
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) utilizza un oggetto di contesto di selezione globale per determinare cosa deve essere visualizzata nell'IDE. Ogni finestra dell'IDE può avere il proprio oggetto di contesto selezione inserito nel contesto di selezione globale. L'IDE aggiorna il contesto di selezione globale con i valori da una finestra quando tale finestra è attiva. Per ulteriori informazioni, vedere [Feedback all'utente](../../extensibility/internals/feedback-to-the-user.md).  
  
 Ogni sito nell'IDE o una cornice di finestra è un servizio denominato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>.</xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> È necessario chiamare l'oggetto creato mediante il pacchetto Visual Studio che viene inserito nella cornice della finestra di `QueryService` metodo per ottenere un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>  
  
 Finestre cornice possono mantenere parti le relative informazioni di contesto di selezione da viene propagata al contesto di selezione globale quando vengono avviate. Questa possibilità è utile per le finestre che potrebbero essere necessario iniziare con una selezione vuota.  
  
 Modifica gli eventi trigger contesto selezione globale in grado di monitorare i package VS. Package VS è possibile eseguire le seguenti attività mediante l'implementazione `IVsTrackSelectionEx` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>interfacce:</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>  
  
-   Aggiornare il file attualmente attivo in una gerarchia.  
  
-   Monitorare le modifiche a determinati tipi di elementi. Ad esempio, se il pacchetto Visual Studio utilizza una speciale **proprietà** finestra, è possibile monitorare le modifiche in attivo **proprietà** finestra e riavviare proprio quando necessario.  
  
 La sequenza seguente descrive il corso tipico della selezione di rilevamento.  
  
1.  L'IDE recupera il contesto di selezione dalla finestra appena aperta e lo inserisce nel contesto di selezione globale. Se il contesto della selezione utilizza HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, tali informazioni non vengono propagate al contesto globale. Per ulteriori informazioni, vedere [Feedback all'utente](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Gli eventi di notifica vengono trasmessi a qualsiasi pacchetto che li ha richiesto.  
  
3.  VSPackage elabora gli eventi che riceve eseguendo attività quali l'aggiornamento di una gerarchia, la riattivazione di uno strumento o altre attività simili.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Selezione e la valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Tipi di progetto](../../extensibility/internals/project-types.md)
