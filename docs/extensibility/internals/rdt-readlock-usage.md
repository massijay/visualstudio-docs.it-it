---
title: Utilizzo di RDT_ReadLock | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 8
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
ms.sourcegitcommit: e7575b914f0645882f3570bdbe29221f2f8130cc
ms.openlocfilehash: a8ea44ef2dea3b3c4ebd29cf95b1886e2028e2c3
ms.lasthandoff: 02/22/2017

---
# <a name="rdtreadlock-usage"></a>Utilizzo di RDT_ReadLock

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>è un flag che fornisce la logica per il blocco di un documento nell'esecuzione di documento tabella (RDT), che corrisponde all'elenco di tutti i documenti attualmente aperti nell'IDE di Visual Studio.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Questo flag determina quando i documenti vengono aperti e se un documento è visibile nell'interfaccia utente o mantenute in modo invisibile in memoria.

In genere, si utilizzerebbe <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>quando uno dei seguenti è true:</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>

- Quando si desidera aprire un documento in modo invisibile e read-only, ma non è stata ancora stabilita quale <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>dovrebbe esserne il proprietario.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

- Quando si desidera che l'utente verrà richiesto di salvare un documento che è stato aperto in modo invisibile prima che venga visualizzato nell'interfaccia utente e quindi ha tentato di chiuderlo.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Come gestire i documenti visibili e invisibili

Quando un utente apre un documento nell'interfaccia utente, un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>proprietario per il documento deve essere stabilita e un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>flag deve essere impostato.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Se nessun <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>proprietario può essere stabilito, quindi il documento non verrà salvato quando l'utente fa clic **Salva tutto** o si chiude l'IDE.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Ciò significa che se si apre un documento in modo invisibile in cui viene modificata in memoria e l'utente viene richiesto di salvare il documento in fase di arresto o salvato se **Salva tutto** viene scelto un `RDT_ReadLock` non può essere utilizzato. In alternativa, è necessario utilizzare un `RDT_EditLock` e registrare un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>quando un <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>flag.</xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock e modifica dei documenti

Il flag precedente menzionato indica che l'apertura del documento invisibile produrrà la `RDT_EditLock` quando il documento viene aperto dall'utente in un oggetto visibile **DocumentWindow**. In questo caso, viene visualizzata con un **salvare** prompt quando visibile **DocumentWindow** viene chiuso. <xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel>implementazioni che utilizzano il <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>servizio funziona inizialmente quando solo un `RDT_ReadLock` (ad esempio, quando il documento viene aperto in modo invisibile per analizzare le informazioni) non viene eseguita.</xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager></xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel> In un secondo momento, se il documento deve essere modificato, quindi il blocco viene aggiornato a un attributo debole **RDT_EditLock**. Se l'utente apre quindi il documento in un oggetto visibile **DocumentWindow**, `CodeModel`del debole `RDT_EditLock` viene rilasciato.

Se l'utente chiude il **DocumentWindow** e sceglie **n** quando viene richiesto di salvare il documento aperto, il `CodeModel` implementazione Elimina tutte le informazioni nel documento e la riapre il documento dal disco in modo invisibile al successivo ulteriori informazioni sono necessarie per il documento. L'accorgimento di questo comportamento è un'istanza in cui l'utente apre il **DocumentWindow** del documento aperto invisibile, modifica, lo chiude e quindi sceglie **n** quando viene richiesto di salvare il documento. In questo caso, se il documento contiene un `RDT_ReadLock`, quindi il documento non viene effettivamente chiuso e il documento modificato resterà aperto in background in memoria, anche se l'utente ha scelto di non salvare il documento.

Se l'apertura del documento invisibile viene utilizzato un debole `RDT_EditLock`, quindi restituisce il relativo blocco quando l'utente apre il documento in modo visibile e non altri blocchi vengono mantenuti. Quando l'utente chiude il **DocumentWindow** e sceglie **n** quando viene richiesto di salvare il documento, il documento deve essere chiuso dalla memoria. Ciò significa che il client invisibile deve attendere gli eventi RDT tenere traccia di questa occorrenza. La volta successiva che il documento è obbligatorio, il documento dovrà essere riaperta.
