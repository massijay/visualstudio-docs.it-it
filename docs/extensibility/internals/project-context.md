---
title: Contesto del progetto | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
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
ms.openlocfilehash: d74d804f65338edb589e63dde111e2ec1a4b5c6f
ms.lasthandoff: 02/22/2017

---
# <a name="project-context"></a>Contesto del progetto
Quando l'utente aggiunge o funziona con i progetti ed elementi del progetto, l'IDE utilizza il concetto di contesto del progetto per determinare come le varie operazioni devono essere eseguite.  
  
 I file sono in genere, gli oggetti di progetto standard che l'utente crea in modo esplicito selezionando il **nuovo progetto** comando o rende disponibili selezionando il **Apri progetto** comando il **File** menu. In questi casi, i file vengono creati e aperte nel contesto di un progetto e il tipo di progetto definisce il contesto per la modifica del documento.  
  
 Alcuni progetti forniscono un contesto molto ricca. Ad esempio, il progetto gestisce una connessione di database con ambito di progetto per l'associazione dati o dello spazio dei nomi con ambito di progetto a livello di codice. L'utente può spesso aprire i file o le connessioni al database direttamente tramite un oggetto particolare progetto, ad esempio un elemento di progetto visualizzato in Esplora soluzioni.  
  
 In altri casi, il contesto del progetto di un elemento non viene specificato in modo esplicito. Ad esempio, il contesto di un elemento non è disponibile quando l'utente apre un file selezionando il **Apri File esistente** comando il **File** menu, quando il debugger viene eseguito su un file, o quando l'utente fa clic il **Cerca nei file** comando il **Trova e sostituisci** la finestra di dialogo. Per gestire queste situazioni, le chiamate IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>per gestire il processo di individuazione il progetto migliore per aprire un documento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>  
  
## <a name="see-also"></a>Vedere anche  
 [Priorità di progetto](../../extensibility/internals/project-priority.md)   
 [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
