---
title: Fornire un contesto di servizio di linguaggio utilizzando l&quot;API Legacy | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
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
ms.openlocfilehash: 10221f77e65acfb91c625c2f711b5804b64f827e
ms.lasthandoff: 02/22/2017

---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Fornire un contesto di servizio di linguaggio utilizzando l'API Legacy
Sono disponibili due opzioni per un servizio di linguaggio fornire contesto dell'utente utilizzando il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale: fornire contesto marcatore di testo o forniscono tutto il contesto utente. In seguito vengono descritte le differenze tra ciascuno.  
  
 Per ulteriori informazioni sulla capacità di fornire contesto a un servizio di linguaggio che è connesso a un editor personalizzato, vedere [procedura: fornire contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Fornire il contesto di marcatore di testo nell'editor  
 Per fornire il contesto per gli errori del compilatore indicati dai marcatori di testo nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor di base, implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>interfaccia.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> In questo scenario, il servizio di linguaggio fornisce il contesto solo quando il cursore si trova su un marcatore di testo. In questo modo l'editor fornire la parola chiave in corrispondenza del cursore ai **Guida dinamica** finestra senza attributi.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Fornire il contesto utente tutti nell'editor  
 Se si sta creando un servizio di linguaggio e utilizza il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di base dell'editor, quindi è possibile implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>interfaccia per fornire il contesto per il servizio di linguaggio.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
 Per l'implementazione di `IVsLanguageContextProvider`, un contenitore del contesto (insieme) è collegato all'editor, responsabile per l'aggiornamento dei contesti. Quando il **Guida dinamica** finestra chiamate di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>interfaccia su questo contenitore del contesto in fase di inattività, il contenitore del contesto richiede l'editor per un aggiornamento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> L'editor notifica quindi al servizio di linguaggio che deve essere aggiornato l'editor e passa un puntatore a contesti. Questa operazione viene eseguita chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>metodo dall'editor per il servizio di linguaggio.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> Usando il puntatore per il contenitore del contesto, il servizio di linguaggio possa aggiungere e rimuovere gli attributi e parole chiave. Per ulteriori informazioni, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
 Esistono due modi diversi per implementare `IVsLanguageContextProvider`:  
  
-   Fornire una parola chiave per il contenitore del contesto  
  
     Quando l'editor viene chiamato per aggiornare il contenitore del contesto, passare gli attributi e parole chiave appropriate e quindi restituire `S_OK`. Il valore restituito indica l'editor per mantenere il contesto (parola chiave) e attributi piuttosto che fornire la parola chiave in corrispondenza del cursore per il contenitore del contesto.  
  
-   Ottenere la parola chiave dalla parola chiave in corrispondenza del cursore  
  
     Quando l'editor viene chiamato per aggiornare il contenitore del contesto, passare gli attributi appropriati e quindi restituire `E_FAIL`. Il valore restituito indica l'editor per mantenere gli attributi in contesti, ma aggiornare il contenitore del contesto con la parola chiave in corrispondenza del cursore.  
  
 Il diagramma seguente illustra come contesto viene fornito per un servizio di linguaggio che implementa `IVsLanguageContextProvider`.  
  
 ![Grafica LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
Contesto per un servizio di linguaggio  
  
 Come può vedere nel diagramma, il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor di testo principale è un contenitore del contesto associato. Questo contenitore del contesto fa riferimento a tre contenitori sottocontesto separato: servizio di linguaggio, editor predefinito e indicatore di testo. Linguaggio del servizio e il testo marcatore sottocontesto sacchi contengono gli attributi e parole chiave per il servizio di linguaggio se il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>interfaccia viene implementata e degli indicatori di testo se il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>interfaccia viene implementata.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> Se non si implementa una di queste interfacce, l'editor fornisce contesto per la parola chiave in corrispondenza del cursore nell'elenco sottocontesto editor predefinito.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Linee guida di contesto per gli editor e finestre di progettazione  
 Editor e finestre di progettazione deve fornire una parola chiave generale per l'editor o la finestra di progettazione. Questa operazione viene eseguita in modo che un argomento della Guida generica, ma appropriato, verrà visualizzato per la progettazione o nell'editor quando si preme F1. Un editor deve, inoltre, la parola chiave corrente in corrispondenza del cursore o forniscano un termine chiave in base alla selezione corrente. Questa operazione viene eseguita per garantire che un argomento della Guida per il testo o un elemento dell'interfaccia utente a cui punta oppure selezionata viene visualizzata quando l'utente preme F1. Una finestra di progettazione fornisce contesto per un elemento selezionato in una finestra di progettazione, ad esempio un pulsante in un form. Gli editor e finestre di progettazione deve inoltre connettersi a un servizio di linguaggio come descritto in [Legacy Language Service Essentials](../extensibility/internals/legacy-language-service-essentials.md).
