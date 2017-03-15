---
title: "Funzionalità fondamentali del servizio di linguaggio legacy | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 21
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
ms.openlocfilehash: f6f8ba46289e27b2465436a103091983c17de1c0
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-language-service-essentials"></a>Funzionalità fondamentali del servizio di linguaggio legacy
È necessario fornire un servizio di linguaggio per integrare un linguaggio di programmazione in Visual Studio. Questo argomento illustra le funzionalità disponibili in servizi di linguaggio legacy.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni sulla nuova modalità per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
 Servizi di linguaggio legacy forniscono le seguenti funzionalità:  
  
|Funzionalità|Descrizione|  
|-------------|-----------------|  
|Colorazione della sintassi|Determina la visualizzazione dell'editor visualizzare diversi colori e gli stili dei caratteri per i vari elementi di una lingua. Questa distinzione può rendere più semplice leggere e modificare i file.<br /><br /> Per informazioni generali, vedere [sintassi colorazione in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Per informazioni su questa funzionalità in framework pacchetto gestito (MPF), vedere [colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Completamento istruzioni|Completa un'istruzione o parola chiave che l'utente ha avviato la digitazione. Completamento delle istruzioni consente agli utenti di immettere istruzioni difficile più facilmente con più rapido e meno probabilità di errore.<br /><br /> Per informazioni generali, vedere [il completamento delle istruzioni in un servizio di linguaggio Legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Per informazioni su questa funzionalità di MPF, vedere [il completamento delle parole in un servizio di linguaggio Legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Corrispondenza parentesi graffe|Novità di rilievo abbinato caratteri, ad esempio le parentesi graffe. Quando l'utente digita un carattere di chiusura, ad esempio "}", corrispondenza parentesi graffe evidenzia corrispondente aprire caratteri, ad esempio "{". Quando sono presenti diversi livelli di caratteri di contenimento, questa funzionalità consente di verificare che i caratteri che lo contiene sono abbinati correttamente.<br /><br /> Per informazioni su questa funzionalità di MPF, vedere [corrispondenza parentesi graffe in un servizio di linguaggio Legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Descrizioni comandi di informazioni di parametro|Visualizza un elenco di possibili firme per il metodo di overload che l'utente attualmente sta digitando.<br /><br /> Per informazioni generali, vedere [informazioni sui parametri in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Per informazioni su questa funzionalità di MPF, vedere [informazioni sui parametri in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Marcatori di errore|Consente di visualizzare una sottolineatura rossa ondulata, noto anche come un ondulate, sotto il testo che è sintatticamente errato. Marcatori di errore in genere vengono utilizzati per informare gli utenti delle parole chiave non digitate correttamente, le parentesi chiuse, caratteri non validi ed errori simili.<br /><br /> Nelle classi MPF di marcatori di errore vengono gestiti automaticamente nel <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>metodo della <xref:Microsoft.VisualStudio.Package.AuthoringSink>classe.</xref:Microsoft.VisualStudio.Package.AuthoringSink> </xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>|  
  
 Molte di queste funzionalità richiedono il servizio di linguaggio per analizzare il codice sorgente. È spesso possibile riutilizzare la suddivisione in token e l'analisi del codice per il compilatore o dall'interprete.  
  
 Le funzionalità seguenti sono correlate per il supporto per linguaggi di programmazione, ma non fanno parte di servizi di linguaggio:  
  
|Funzionalità|Descrizione|  
|-------------|-----------------|  
|Analizzatori di espressioni|Supporta il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger convalida i punti di interruzione e fornendo un elenco di espressioni da visualizzare nella **Auto** finestra di debug.<br /><br /> Per ulteriori informazioni, vedere [Language supporto del servizio per il debug](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Strumenti di esplorazione di simbolo|Supporta **Visualizzatore oggetti**, **Visualizzazione classi**, **Visualizzatore chiamate**, e **risultati ricerca simbolo**.|
