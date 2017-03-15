---
title: Linee guida di controllo di origine aggiuntivi per progetti ed editor | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
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
ms.openlocfilehash: ee74f16c90dbf697732a490f895efb1a52233d80
ms.lasthandoff: 02/22/2017

---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Linee guida di controllo di origine aggiuntivi per progetti ed editor
Esistono alcune linee guida che progetti ed editor deve avere per supportare il codice sorgente.  
  
## <a name="guidelines"></a>Indicazioni  
 Il progetto o l'editor deve anche eseguire le operazioni seguenti per il supporto di controllo del codice sorgente:  
  
|Area|Progetto|Editor|Dettagli|  
|----------|-------------|------------|-------------|  
|Privato copie dei file|x||L'ambiente supporta private copie dei file. Ogni persona integrato nel progetto, ovvero ha proprio propria copia privata dei file nel progetto.|  
|Persistenza ANSI o Unicode|x|x|Se si scrive il codice di persistenza, vengono mantenuti i file in formato ANSI poiché la maggior parte dei programmi di controllo di origine al momento non supportano Unicode.|  
|Enumerare i file|x||Il progetto deve contenere un elenco specifico di tutti i file in esso contenuti e deve essere in grado di enumerare l'elenco dei file utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(VSH_PROPID_First_Child/Next_Sibling).</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Il progetto deve inoltre esporre i nomi di elemento tramite il relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>implementazione e supporto di ricerca del nome (inclusi file speciali) tramite il relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>implementazione.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>|  
|Formato testo|x|x|Quando possibile, i file devono essere in formato testo per supportare l'unione di versioni diverse. Impossibile unire file che non sono in formato testo con altre versioni del file in un secondo momento. Il formato di testo preferito è XML.|  
|Basato sul riferimento|x||Progetti basato sul riferimento facilmente sono supportati nel controllo del codice sorgente. Tuttavia, progetti basati su directory sono supportati anche dal controllo del codice sorgente, purché il progetto può produrre un elenco dei file su richiesta, indipendentemente dall'esistano di tali file sul disco. Quando si apre un progetto dal controllo del codice sorgente, il file di progetto diventa inattivo prima di qualsiasi file.|  
|Rendere persistenti gli oggetti e proprietà in ordine prevedibile|x|x|Mantenere i file in un ordine prestabilito, ad esempio ordine alfabetico, per facilitare l'unione.|  
|Ricarica|x|x|Quando viene modificato un file su disco, l'editor deve essere in grado di ricaricare il file. Quando partecipa a controllo del codice sorgente, l'ambiente ricarica dati per l'utente chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>implementazione.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Il caso di ricarica più difficile è quando si verifica un checkpoint quando è stato chiamato IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e l'elaborazione di informazioni.</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Tuttavia, il codice di caricamento deve essere in grado di eseguire in questa situazione.<br /><br /> L'ambiente ricarica automaticamente i file di progetto. Tuttavia, è necessario implementare un progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>se è nidificata gerarchie per supportare il ricaricamento annidati file di progetto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
