---
title: Servizi per linguaggi e l&quot;Editor di componenti di base | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
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
ms.openlocfilehash: c78c3c5e450ffe348a8af2687e2b9b30b1128e8e
ms.lasthandoff: 02/22/2017

---
# <a name="language-services-and-the-core-editor"></a>Servizi per linguaggi e l'Editor di componenti di base
Gli editor in Visual Studio sono spesso associati a un servizio di linguaggio. Tra le altre cose, un servizio di linguaggio fornisce la colorazione della sintassi, il completamento delle istruzioni, IntelliSense e la formattazione del testo.  
  
## <a name="core-editors-and-document-data-objects"></a>Editor di componenti di base e oggetti dati documento  
 Quando si accede a editor principale, non di creare oggetti di visualizzazione di documenti e dati del documento. L'IDE crea e controlla questi due oggetti e per ottenere l'handle, che effettua le chiamate appropriate nell'editor di implementazione della factory.  
  
 Per ulteriori informazioni, vedere [determinare quale Editor apre un File in un progetto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Servizi per linguaggi e l'Editor di componenti di base  
 Implementando un servizio di linguaggio, è possibile controllare la modalità di visualizzazione dei dati nella visualizzazione dei documenti. Un servizio di linguaggio fornisce informazioni e il comportamento specifico per una determinata lingua, ad esempio Visual C++. Quando si crea un buffer di testo e determinare l'estensione per il documento aperto, il buffer di testo determina il servizio di linguaggio associato a questa estensione del nome file da una chiave del Registro di sistema, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors\\\Extensions {GUID YourLanguageService}. Standard VSPackage caricamento procedura quindi carica il pacchetto Visual Studio e viene creata un'istanza del servizio di linguaggio.  
  
 Nella figura seguente è illustrato un servizio di linguaggio di base.  
  
 ![Rappresentazione grafica di Language Service Model](~/extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Oggetti servizio editor e della lingua di base  
  
 L'oggetto dati di documento per l'editor di componenti di base viene chiamato un buffer di testo ed è rappresentato dal <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>oggetto.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> L'oggetto di visualizzazione del documento è una visualizzazione di testo ed è rappresentato dal <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>oggetto.</xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Questi due oggetti interagiscono tramite il servizio di linguaggio per offrire una vista unificata dell'editor di componenti di base. Le informazioni dal buffer di testo e la visualizzazione di testo viene visualizzata in una finestra del documento denominato codice. Il documento di finestra di codice è gestito da un gestore di finestra di codice.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Fornire un contesto di servizio di linguaggio utilizzando l'API Legacy](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hosting di IntelliSense](../extensibility/intellisense-hosting.md)   
 [Lingue indipendente](../extensibility/contained-languages.md)   
 [Sviluppo di un servizio di linguaggio Legacy](../extensibility/internals/developing-a-legacy-language-service.md)
