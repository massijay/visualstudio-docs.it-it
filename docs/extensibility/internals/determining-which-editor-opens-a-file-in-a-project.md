---
title: Determinare quale Editor apre un File in un progetto | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ac16b6f4d8429d328cfd76b8b02cd1620f4a4294
ms.lasthandoff: 02/22/2017

---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Determinazione di un File in un progetto che verrà aperto l'Editor
Quando un utente apre un file in un progetto, l'ambiente passa attraverso un processo di polling, infine aprire l'editor appropriato o la finestra di progettazione per il file. La procedura iniziale impiegata dall'ambiente è lo stesso per editor standard e personalizzate. L'ambiente utilizza una serie di criteri durante il polling quale editor da utilizzare per aprire un file e VSPackage deve coordinare con l'ambiente durante questo processo.  
  
 Ad esempio, quando un utente seleziona il **aprire** comando il **File** dal menu e quindi sceglie `filename`. RTF (o qualsiasi altro file con estensione RTF), l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>implementazione per ogni progetto, alla fine ciclicamente tutte le istanze di progetto nella soluzione.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Progetti di restituiscono un set di flag che specificano le attestazioni in un documento in base alla priorità. Usa la priorità più alta, l'ambiente chiama appropriato <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>metodo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Per ulteriori informazioni sul processo di polling, [aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Progetto di file esterni attestazioni tutti i file non richiesti da altri progetti. In questo modo, editor personalizzati possibile aprire documenti prima di poterli aprire Editor standard. Se un progetto di file esterni dichiara un file, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>metodo per aprire il file con un editor standard.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> L'ambiente controlla l'elenco interno di editor registrato per uno che gestisce i file RTF. Questo elenco si trova nella seguente chiave del Registro di sistema:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{`editor factory guid`>} \Extensions]  
  
 L'ambiente controlla anche gli identificatori di classe nella chiave HKEY_CLASSES_ROOT\CLSID per tutti gli oggetti che dispongono di una sottochiave DocObject. Se viene trovato l'estensione di file, una versione incorporata dell'applicazione, ad esempio Microsoft Word, viene creata sul posto in Visual Studio. Questi oggetti documento devono essere file compositi che implementano il <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>interfaccia o l'oggetto deve implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> </xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>  
  
 Se non vi è nessuna factory editor per i file RTF nel Registro di sistema, quindi l'ambiente di ricerca nella chiave HKEY_CLASSES_ROOT \\chiave RTF e verrà aperto l'editor specificato non esiste. Se l'estensione di file non viene trovato in HKEY_CLASSES_ROOT, l'ambiente utilizza l'editor di testo principale di Visual Studio per aprire il file se si tratta di un file di testo.  
  
 Se l'editor di testo di base non riesce, che si verifica che se il file non è un file di testo, l'ambiente utilizza il relativo editor binario per il file.  
  
 Se l'ambiente di trovare un editor per l'estensione RTF nel relativo Registro di sistema, carica il package VS che implementa questa factory editor. L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>metodo sul nuovo VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Le chiamate di VSPackage `QueryService` per `SID_SVsRegistorEditor`, usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>metodo per registrare la factory editor con l'ambiente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>  
  
 A questo punto l'ambiente di verifica nuovamente l'elenco interno di editor registrato per trovare la factory editor appena registrato per i file RTF. L'ambiente chiama l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>metodo passando il tipo di nome e la visualizzazione di file da creare.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat></xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage></xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
